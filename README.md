<div align="center">

## graphics demo


</div>

### Description

It draws lines on the screen. Looks like a screensaver. Shows some basic C++ coding techniques.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Doug Jones](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/doug-jones.md)
**Level**          |Beginner
**User Rating**    |3.0 (12 globes from 4 users)
**Compatibility**  |C\+\+ \(general\), Borland C\+\+
**Category**       |[Graphics/ Sound](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics-sound__3-15.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/doug-jones-graphics-demo__3-1191/archive/master.zip)





### Source Code

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>
#include <dos.h>
int main(void)
{
	int x1, y1, x2, y2;
	int a1, b1, a2, b2;
	int xadd1 = 3, yadd1 =1, xadd2 = 5, yadd2 =2;
	int whichColor=1;
	int arx1[101] = {0};
	int arx2[101] = {0};
	int ary1[101] = {0};
	int ary2[101] = {0};
	int ara1[101] = {0};
	int ara2[101] = {0};
	int arb1[101] = {0};
	int arb2[101] = {0};
	int counter = 0;
	int counter2 = 0;
	/* request auto detection */
	int gdriver = DETECT, gmode, errorcode;
	/* initialize graphics mode */
	initgraph(&gdriver, &gmode, "c:\\tc\\bgi\\");  /* path is the location of the egavga.bgi file, might be different on your comp...if you get an error about this file not being found you know why */
	/* read result of initialization */
	errorcode = graphresult();
	if (errorcode != grOk) /* an error occurred */
	{
		printf("Graphics error: %s\n", grapherrormsg(errorcode));
		printf("Press any key to halt:");
		getch();
		exit(1);    /* return with error code */
	}
		/* draw a line */
	x1 = 0;
	y1 = 0;
	x2= 0;
	y2 = 0;
	a1 = getmaxx();
	b1 = 0;
	a2 = getmaxx();
	b2 = 0;
	while(!kbhit())
	{
		line(x1, y1, x2, y2);
		line(a1, b1, a2, b2);
		arx1[counter] = x1;
		ary1[counter] = y1;
		arx2[counter] = x2;
		ary2[counter] = y2;
		ara1[counter] = a1;
		ara2[counter] = a2;
		arb1[counter] = b1;
		arb2[counter] = b2;
		if (counter2 > 100)
		{
			setcolor(0);
			if (counter < 100)
			{
				line(arx1[counter + 1], ary1[counter + 1], arx2[counter + 1], ary2[counter + 1]);
				line(ara1[counter + 1], arb1[counter + 1], ara2[counter + 1], arb2[counter + 1]);
			}
			if (counter == 100)
			{
				line(arx1[0], ary1[0], arx2[0], ary2[0]);
				line(ara1[0], arb1[0], ara2[0], arb2[0]);
			}
			setcolor(whichColor);
		}
		if (x1 > (getmaxx()/2) || x1 <0)
			xadd1 *= -1;
		if (x2 > (getmaxx()/2) || x2 < 0)
			xadd2 *= -1;
		if (y1 > getmaxy() || y1 < 0)
			yadd1 *= -1;
		if (y2 > getmaxy() || y2 < 0)
			yadd2 *= -1;
			x1 += xadd1;
			x2 += xadd2;
			y1 += yadd1;
			y2 += yadd2;
			a1 += xadd1 * -1;
			a2 += xadd2 * -1;
			b1 += yadd1;
			b2 += yadd2;
			counter++;
			if(counter2 < 101)
				counter2++;
			if (counter % 100 == 0)
			{
				if(whichColor > getmaxcolor())
					whichColor = 1;
				whichColor += 1;
				setcolor(whichColor);
			}
			if (counter > 100)
				counter = 0;
			delay(10);
	}
 /* clean up */
 getch();
 closegraph();
 return 0;
}
```

