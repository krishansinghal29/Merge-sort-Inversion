/*
// Sample code to perform I/O:

#include <iostream>

using namespace std;

int main() {
	int num;
	cin >> num;										// Reading input from STDIN
	cout << "Input number is " << num << endl;		// Writing output to STDOUT
}

// Warning: Printing unwanted or ill-formatted data to output will cause the test cases to fail
*/

// Write your code here
#include <iostream>
#include <vector>
using namespace std;
long int count=0;

vector<int> mergearr(vector<int> A,vector<int> B){
    int n1=A.size();
    int n2=B.size();
    vector<int> C(n1+n2);
    int i=0;int j=0;int k=0;
    while(i<n1&&j<n2){
        if(A[i]<B[j]){
            C[k]=A[i];k++;i++;
        }
        else{
            C[k]=B[j];k++;j++;
        }
    }
    if(i==n1){
        while(j<n2){
            C[k]=B[j];k++;j++;
        }
    }
    else{
        while(i<n1){
            C[k]=A[i];k++;i++;
        }
    }
    return C;
}

vector<int> mergesort(vector<int> Ar){
    int n=Ar.size();
    if(n==1){
        return Ar;
    }
    else{
        vector<int> A(n/2);
	    vector<int> B(n-(n/2));
	    for(int i=0;i<n/2;i++){
	        A[i]=Ar[i];
	    }
	    for(int i=n/2;i<n;i++){
	        B[i-n/2]=Ar[i];
	    } 

	    A=mergesort(A);
	    B=mergesort(B);
	    int j=0;
	    int reslt=0;
	    for(int i=0;i<n/2;i++){
            while((A[i]>2*B[j])&&(j<n-n/2)){
                j++;
            }
            reslt=reslt+j;
        }
        count=count+reslt;
	    return mergearr(A,B);
    }
}
/*vector<int> mergesort(vector<int> Ar){
    int n=Ar.size();
    if(n==1){
        return Ar;
    }
    else{
        vector<int> A(n/2);
	    vector<int> B(n-(n/2));
	    for(int i=0;i<n/2;i++){
	        A[i]=Ar[i];
	    }
	    for(int i=n/2;i<n;i++){
	        B[i-n/2]=Ar[i];
	    } 
	    //vector<int> A1(n/2);
        //vector<int> B1(n-n/2);
	    A=mergesort(A);
	    B=mergesort(B);
	    return mergearr(A,B);
    }
}*/
/*int inv(vector<int> A,vector<int> B){
    int reslt=0;
    int n1=A.size();
    int n2=B.size();
    int j=0;
    //vector<int> A1(n1);
    A=mergesort(A);
    //vector<int> B1(n2);
    B=mergesort(B);
    for(int i=0;i<n1;i++){
        while((A[i]>2*B[j])&&(j<n2)){
            j++;
        }
        reslt=reslt+j;
    }
    return reslt;
}
int inversion(vector<int> Ar){
    int n=Ar.size();
    if(n==1){
        return 0;
    }
    else{
        vector<int> A(n/2);
	    vector<int> B(n-n/2);
	    for(int i=0;i<n/2;i++){
	        A[i]=Ar[i];
	    }
	    for(int i=n/2;i<n;i++){
	        B[i-n/2]=Ar[i];
	    } 
	    int a=inversion(A);
	    int b=inversion(B);
	    int c=inv(A,B);
	    //printf("%ld %ld %ld ",a,b,c);
	    return a+b+c;
    }
}*/

int main() {
	int numtest;
	cin >> numtest;								
	for(int i=0 ;i<numtest;i++){
	    int num;
	    cin >> num;
	    vector<int> A(num);
        for(int i=0;i<num;i++){
	        cin >> A[i];
	    }
	    mergesort(A);
	    printf("%ld\n",count);
	    count=0;
	}	
	return 0;
}
