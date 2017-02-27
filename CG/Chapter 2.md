# CG: Chapter 2

# Output primitives
## Line drawing
### DDA algorithm (digital differential analyser)
- For any line, y = mx + c,
	- If we take delta(x) = 1, y = y’ &#177; m
	- If we take delta(y) = 1, x = x’ &#177; m
- In DDA, algorithm, unit steps are taken in x or y direction depending on whether dx > dy. The greater difference is chosen as the overall length
- Then x and y are calculated as - 
	xinc = dx/length, yinc = dy/length
- x and y are incremented by their respective properties till unit steps are taken length times.
![DDA Algorithm](/CG/images/DDA_ALGO.png)

### Bresenham’s Line algorithm
- Finds the error distance between two pixels and the actual point on the line
- The smaller distance is chosen and then the new error is calculated
- Unit steps are taken in x 
- The leftmost point is chosen as the start point
![Bresenham algorithm](/CG/images/BRESENHAM_ALGO.png)

## Circle drawing 
### Midpoint circle algorithm
- We know that for a circle S(x,y), if x’, y’ are real values
	- if S(x’, y’) < 0, x’, y’ lies inside the circle
	- S(x’,y’) = 0, x’, y’ lies on the circle
	- S(x’,y’) > 0, x’, y’ lies outside the circle
- In midpoint algorithm, this property is used to find whether the upper or lower pixel should be plotted
![Midpoint circle illustration](/CG/images/MIDPOINT_CIRCLE.png)
- The midpoint between two points (xk+1, yk) and (xk+1, yk+1) is (xk+1, yk+0.5)
- By plugging in this value inside the circle’s equation, we can find if the midpoint lies inside or outside/on the circle
- If it lies inside the circle then (xk+1, yk) is the correct pixel to plot.
- Thus at every step we can find the correct pixel to plot 
- As a circle has infinite lines of symmetry we can use this property to reduce computations required to plot it. Only the calculations for the first quadrant are made, then the other 7 quadrants are plotted symmetrically. 
-  Thus the ending point is when tan(theta) = 1, i.e., x = y
![Midpoint Circle Algorithm](/CG/images/MIDPOINT_CIRCLE_ALGO.png)

## Ellipse drawing
### Midpoint ellipse algorithm
- The midpoint ellipse algorithm uses the same concept as midpoint circle algorithm - at every iteration it finds whether the midpoint of two critical pixels is within or outside/on the curve and chooses accordingly.
- However, the x increment cannot be unit wise after abs(dy/dx) > 1
- This is because the rate of increase of y is not greater than x.
- As we plot the first quadrant (the rest are done symmetrically), the condition for separation of regions is dy/dx = -1.
- At this point,  x(b^2) > y(a^2)
- Thus in region 1, abs(dy/dx) < 1,  x is incremented unit wise. In region 2, y is incremented unit wise and decisions are made between xk, yk+1 and xk+1, yk+1.

![Midpoint Ellipse Region 1](/CG/images/MIDPOINT_ELLIPSE_1.png)
![Midpoint Ellipse Region 2](/CG/images/MIDPOINT_ELLIPSE_2.png)

``` c
void ellipseMidpoint(float xc, float yc, float a, float b)
{
    float aSq = a * a;
    float bSq = b * b;
    float x = 0, y = ry, p;
    float px = 0, py = 2 * aSq * y;

    drawEllipse(xc, yc, x, y);

    //Region 1
    p = aSq - (aSq * b) + (0.25 * aSq);

    while (px < py)
    {
        x++;
        px = px + 2 * bSq;
        if (p < 0)
            p = p + bSq + px;
        else
        {
            y—;
            py = py - 2 * aSq;
            p = p + bSq + px - py;
        }

        drawEllipse(xc, yc, x, y);
    }

    //Region 2
    p = bSq*(x+0.5)*(x+0.5) + aSq*(y-1)*(y-1) - aSq*bSq;

    while (y > 0)
    {
        y—;
        py = py - 2 * aSq;
        if (p > 0)
            p = p + aSq - py;
        else
        {
            x++;
            px = px + 2 * bSq;
            p = p + aSq - py + px;
        }
        drawEllipse(xc, yc, x, y);
    }
}
```