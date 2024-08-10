# 3-floyd-and-warshall


Warshall’s Algorithm:
#include<conio.h>
#include<stdio.h>
int a[10][10],n;
void warshalls();
void main()
{
int i,j;
printf("\n Enter the no. of vertices:\t");
scanf("%d",&n);
printf("\n Enter the adjacency matrix:\n");
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
scanf("%d",&a[i][j]);
}
}
warshalls();
}
void warshalls()
{
int i,j,k;
for(k=1;k<=n;k++)
{
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
if(a[i][j]!=1)
{
if(a[i][k]==1&&a[k][j]==1)
{
a[i][j]=1;
}
}
}
}
}
printf("\n Path matrix is:\n");
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
printf("%d\t",a[i][j]);
}
printf("\n\n");
}
}
9.
Floyd’s Algorithm:
#include<stdio.h>
#include<sys/time.h>
#include<stdlib.h>
#include<unistd.h>
int n,c[10][10],d[10][10];
int min(int,int);
void read_data();
void write_data();
void floyds();
void write_data()
{
int i,j;
printf("the least distance matrix is\n ");
for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
{
printf("%d\t",d[i][j]);
}
printf("\n");
}
}
void floyds()
{
int i,j,k;
for(i=0;i<n;i++)
for(j=0;j<n;j++)
d[i][j]=c[i][j];
for(k=0;k<n;k++)
{
for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
{
d[i][j]=min(d[i][j],d[i][k]+d[k][j]);
}
}
}
}
int min(int a,int b)
{
if(a<b)
return a;
return b;
}
void read_data()
{
int i,j;
printf("enter the number of vertices\n");
scanf("%d",&n);
printf("enter the cost matrix\n");
for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
{
scanf("%d",&c[i][j]);
}
}
}
int main()
{
read_data();
floyds();
write_data();
}
