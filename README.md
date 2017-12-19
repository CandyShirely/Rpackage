# Rpackage
A simple package about algorithm

Actually, at first, i want to create a more complicated one. But, unfortunately, i failed. The things below are what i want to introduce to Rpackages. And i hope someone will help me make it if it's possible.
#include <iostream>
#include <cstring>
#include <ctime>
#include <cstdlib>
#include <algorithm>
const int MAXN = 10000000+10;
using namespace std;
int A[MAXN];
int n;

void quicksort(int *A,int l,int r){//sort number in array A
	if(r<=l)return;//if r-l<=1 then return
	swap(A[rand()%(r-l)+l+1],A[l]);
	int mid=(l+r)>>1,cmp=A[l],loc=l;
	for(int i=l+1;i<=r;i++)//use for loop to realize qsort
		if(A[i]<cmp || (A[i]==cmp && loc<mid)){
			loc++;
			if(i!=loc)swap(A[i],A[loc]);
		}
	quicksort(A,l,loc-1);
	quicksort(A,loc+1,r);
}

int main(){
	srand(time(NULL));
	n=1000000;
	//n=100;
	for(int i=0;i<n;i++)A[i]=rand();
	//for(int i=0;i<n;i++)cout<<A[i]<<" ";cout<<endl;
	quicksort(A,0,n-1);
	//for(int i=0;i<n;i++)cout<<A[i]<<" ";cout<<endl;
	return 0;
}
