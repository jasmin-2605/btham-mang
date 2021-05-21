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















