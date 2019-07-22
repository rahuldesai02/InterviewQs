# Implementing n stacks using Array

```c++
#include<bits/stdc++.h>
using namespace std;

//Approach 1 Fixed Allocation
class FixedMultiStack
{
public:
	int noOfStack;
	int stackCapacity;
	int *values;
	int *sizes;
	FixedMultiStack(int stacksize,int n)
	{
		n = noOfStack;
		stackCapacity=stacksize;
		values = new int[stacksize*noOfStack];
		sizes = new int[noOfStack];
	}
	int getTop(int stackNo)
	{
		int offset = stackNo*stackCapacity;
		int size = sizes[stackNo];
		return offset + size -1;
	}
	bool isFull(int stackNo)
	{
		return sizes[stackNo]==stackCapacity;
	}	
	bool isEmpty(int stackNo)
	{
		return sizes[stackNo]==0;
	}
	void push(int stackNo,int value)
	{
		if(isFull(stackNo)){
			cout<<"Stack "<<stackNo<<" Full"<<"\n";
			return;
		}
		sizes[stackNo]++;
		values[getTop(stackNo)]=value;
	}
	int pop(int stackNo)
	{
		if(isEmpty(stackNo)){
			cout<<"Stack "<<stackNo<<" Empty\n";
			return -1;
		}
		int top = getTop(stackNo);
		int value = values[top];
		values[top]=0;
		sizes[stackNo]--;
		return value;
	}
	void displayStack(int stackNo)
	{
		if(isEmpty(stackNo)){
			cout<<"Empty\n";
			return;
		}
		for(int i = stackNo*stackCapacity;i<=getTop(stackNo);i++){
			cout<<values[i]<<" ";
		}
		cout<<"\n";
	}	
};
void display(FixedMultiStack &M)
{
	for(int i=0;i<3;i++)
	{
		M.displayStack(i);
	}
	cout<<"\n";
}


int main()
{

    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    FixedMultiStack M = FixedMultiStack(3,3) ;
    M.push(0,1);
    M.push(0,2);
    M.push(0,3);
    M.push(0,4);
    M.push(1,5);
    M.push(2,6);
    int y = M.pop(2);
    y = M.pop(2);
    int x = M.pop(0);
    watch(x);
    display(M);

    return 0;
}
```

