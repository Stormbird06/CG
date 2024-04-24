#include<iostream>
#include<GL/glut.h>
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
using namespace std;
int xc=300,yc=300;
void displayPoint(int x,int y)
{
glColor3f(0,1,0);
glPointSize(2);
glBegin(GL_POINTS);
glVertex2i(x,y);
glEnd();
}
void SimpleLine(float x1,float y1,float x2,float y2)
{
float step;
float dx = x2-x1;
float dy = y2-y1;
if(abs(dx)>= abs(dy))
{
step=abs(dx);
}
else
step =abs(dy);
float Xinc =dx/(float) step;
float Yinc =dy/(float) step;
float x=x1;
float y=y1;
for(int i=0;i<=step;i++)
{
displayPoint(x,y);
x=x+Xinc;
y=y+Yinc;
}
glFlush();
}
void plotPoint(int xc,int yc,int x,int y)
{
glColor3f(0,1,1);
glPointSize(2);
glBegin(GL_POINTS);
glVertex2i(xc+x,yc+y);
glVertex2i(xc+y,yc+x);
glVertex2i(xc-x,yc+y);
glVertex2i(xc-y,yc+x);

glVertex2i(xc-x,yc-y);
glVertex2i(xc-y,yc-x);
glVertex2i(xc+x,yc-y);
glVertex2i(xc+y,yc-x);
glEnd();
}
void midpoint(int xc,int yc,int radius)
{
int x=0;
int y=radius;
plotPoint(xc,yc,x,y);
int p=1-radius;
do{
if(p<0)
{
x++;
p=p+2*x+1;
}
if(p>=0)
{
x++;
y--;
p=p+2*(x-y)+1;
}
plotPoint(xc,yc,x,y);
}while(x<=y);
glFlush();
}
void keyboard(unsigned char key,int x,int y)
{
switch(key)
{
case 's':
glClearColor(1.0,1.0,1.0,1.0);
glClear(GL_COLOR_BUFFER_BIT);
midpoint(xc,yc,100);
break;
case 'c':
glClearColor(1.0,1.0,1.0,1.0);
glClear(GL_COLOR_BUFFER_BIT);
midpoint(xc,yc,50);
midpoint(xc,yc,200);
break;
case 'f':
glClearColor(1.0,1.0,1.0,1.0);
glClear(GL_COLOR_BUFFER_BIT);
midpoint(xc,yc,100);
midpoint(xc+100,yc,100);
midpoint(xc-100,yc,100);
midpoint(xc,yc-100,100);
midpoint(xc,yc+100,100);
break;

}

glutPostRedisplay();
}
void initialize()
{
glClearColor(1.0,1.0,1.0,1.0);
glClear(GL_COLOR_BUFFER_BIT);
gluOrtho2D(0,600,600,0);
}
void primitives(void)
{
glColor3f(1,0,0);
SimpleLine(0,300,600,300);
SimpleLine(300,0,300,600);
glutKeyboardFunc(keyboard);
}
int main(int argc,char **argv)
{
glutInit(&argc,argv);
glutInitDisplayMode(GLUT_SINGLE);
glutInitWindowPosition(0,0);
glutInitWindowSize(600,600);
glutCreateWindow("Circle");
initialize();
cout<<"s:Simple Circle";
cout<<"\n c: Concentric Circle";
cout<<"\n f: Intersecting Circle";
glutDisplayFunc(primitives);
glutMainLoop();
return 0;
}
