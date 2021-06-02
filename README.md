# btham-mang


//bai 6

#include <stdio.h>
#include <stdlib.h>
#include<math.h>

void nhap(int a[],int m)
{
    for (int i=0; i<m; i++)
    {

            printf("a[%d]:",i);
            scanf("%d",&a[i]);
        }
    }

void xuat(int a[0],int m)
{
    for(int i=0; i<m; i++)
    {

            printf("%3d",a[i]);

    }
}
int ktraSNT(int n)
{
    int uoc=0;
    for (int i=1; i<=n; i++)
    {
        if(n%i==0)
            uoc++;
    }
    if(uoc==2)
        return 1;
    else
        return 0;
}

void tongSNT(int a[],int m){
    int s=0;
    for (int i=0; i<m; i++)
{

            if (ktraSNT(a[i])==1)
            {
                s+=a[i];
            }

    }
    printf("\nTong SNT la: %d",s);
}

int main()
{
    int a[50];
    int m;
    scanf("%d",&m);
    nhap(a,m);
    xuat(a,m);
    tongSNT(a,m);

}



\\bai 7

#include <stdio.h>
#include <stdlib.h>


void nhap(int a[],int m){
      for (int i=0;i<m;i++)
           scanf("%d",&a[i]);

}

void xuat(int a[],int m){
      for(int i=0;i<m;i++)
        printf("%4d ",a[i]);

}

void soduong(int a[],int b[],int m,int *h){

   for (int i=0; i<m;i++){
    if(a[i]>=0){
       b[*h]=a[i];
        (*h)++;
    }
   }
}

void soam(int a[],int c[],int m,int *g){


   for (int i=0; i<m;i++){
    if(a[i]<0){
        c[*g]=a[i];
        (*g)++;
    }
   }

}

int main(){
    int a[50];
    int b[50];
    int c[50];
    int n;
    int l=0,k=0;
    scanf("%d",&n);
    nhap(a,n);
    xuat(a,n);
    soduong(a,b,n,&l);
    printf("\n");
    xuat(b,l);
    soam(a,c,n,&k);
    printf("\n");
    xuat(c,k);

}


//bai 8
#include<stdio.h>


int tinh(int x, int n){
	if ( n==1)
	     return x;
	else  
	    return x*tinh(x,n-1);
}

int giaiThua(int n)
{
   
    if (n == 1)
        return 1;
    else
        return (n) * giaiThua(n - 1);
}


int main (){

int x,n;
int m;
printf("nhap ham f(x,n)=x^n:");
scanf("%d%d",&x,&n);

printf("nhap n de tinh s(n)=(2n)!:");
scanf("%d",&m);
m=m*2;
printf("%d\n",tinh(x,n));
printf("%d", giaiThua(m));
}



//bai 9

#include<stdio.h>

int d=1;
void topright(int [][50],int ,int , int , int );

void bottomleft(int [][50], int , int , int , int );


void topright (int a[][50],int x1, int y1, int x2, int y2){
	for (int i=x1;i<=x2;i++)
		a[y1][i]=d++;			
	for (int j=y1+1;j<=y2;j++)
	    a[j][x2]=d++;
	
	if (x2-x1>0&&y2-y1>0){
		y1++;
		x2--;
	   bottomleft(a,x1,y1,x2,y2);
	}
	
}

void bottomleft(int a[][50],int x1,int y1, int x2, int y2){
	for(int i=x2;i>=x1;i--)
	    a[y2][i]=d++;
	for(int j=y2-1;j>=y1;j--)  
	    a[j][x1]=d++;
	if(x2-x1>0&&y2-y1>0){
		y2--;
		x1++;
		topright(a,x1,y1,x2,y2);
	}
}

void xuat(int a[][50],int n, int m)
{
	for (int i=0;i<n;i++)
	{
		for (int j=0;j<m;j++){
			printf("%4d", a[i][j]);
		}
		printf("\n");
	}
}


int main(){
	int a[50][50];
	int m,n;
	printf("moi ban nhap so hang:");
	scanf("%d",&n);
	printf("moi ban nhap so cot:");
	scanf("%d",&m);
	topright(a,0,0,m-1,n-1);
	xuat(a,n,m);
	
}

// bai 10

#include <stdio.h>
#include <stdlib.h>


#include<math.h>

void NhapDaThuc(int a[],int n)

{
    for(int i=0; i<=n; i++)
    {
        scanf("%d",&a[i]);

    }

}
void indathuc(int a[],int n){
      for(int i=n;i>=1;i--)
        printf("%dX%d + ",a[i],i);

printf("%d ",a[0]);
printf("\n");
}

void TinhGT(int a[],int n,int x){
    int s=0;
    for (int i=n;i>=1;i--)
         s+=a[i]*x;
s+=a[0];
 printf("%d\n", s);
}

void tonghaidathuc(int a[],int b[],int c[],int n, int m){
    int i;
     for (i=0;i<= ((n<m)?m:n) ;i++)
            c[i]= ((i<=n)?a[i]:0) + ((i<=m)?b[i]:0);

        printf("\nCac he so da thuc T=P+Q la:");
        for(i= ((n>m)?n:m);i>=0;i--)
                printf("%d ",c[i]);




}
int main(){
    int P[50], Q[50],T[50];
    int m,n,x;
    printf("moi ban nhap bac da thuc P va Q: ");
    scanf("%d%d",&n,&m);
    NhapDaThuc(P,n);
    NhapDaThuc(Q,m);
    printf("nhap gia tri x: ");
    scanf("%d",&x);
    printf("gia tri cua da thuc P: ");
    TinhGT(P,n,x);
    printf("gia tri cua da thuc Q: ");
    TinhGT(Q,m,x);
    tonghaidathuc(P,Q,T,n,m);
    printf("\nhe so da thuc P,Q,T la:\n");
    printf("P = ");
    indathuc(P,n);
    printf("Q = ");
    indathuc(Q,m);
    printf("T = ");
    indathuc(T,n>m?n:m);
}

//bai 11 






















