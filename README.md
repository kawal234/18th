# 18th

#include<iostream>
#include<vector>
using namespace std;

//Q1. Prefix sums in 2d arrays

// int rectangleSum (vector<vector<int>> &matrix, int l1,int r1,int l2,int r2){
//     int sum=0;
//     for(int i=l1;i<=l2;i++){
//         for(int j=r1;j<=r2;j++){
//             sum+=matrix[i][j];
//         }
//     }
//     return sum;
// }

// int main(){
//     int n,m;
//     cin>>n>>m;
//     vector <vector<int > > matrix(n,vector<int> (m));

//     for(int i=0;i<n;i++){
//         for(int j=0;j<m;j++){
//             cin>>matrix[i][j];
//         }
//     }

//     int l1,r1,l2,r2;
//     cout<<"Enter the range of rows and columns to find prefix sum: ";
//     cin>>l1>>r1>>l2>>r2;
//     for(int i=0;i<n;i++){
//         for(int j=0;j<m;j++){
//             cout<<matrix[i][j]<<" ";
//         }cout<<endl;
//     }

//     int sum = rectangleSum(matrix,l1,r1,l2,r2);
//     cout<<"Sum: "<<sum<<endl;
//     return 0;
// }


//Q2. prefix sum matrix (row-wise)

int rectangleSum (vector<vector<int>> &matrix, int l1,int r1,int l2,int r2){
    int sum=0;
    // for(int i=l1;i<=l2;i++){
    //     for(int j=r1;j<=r2;j++){
    //         sum+=matrix[i][j];
    //     }
    // }
// prefix sum array row-wise
    for(int i=0;i<=matrix.size();i++){
        for(int j=1;j<=matrix.size();j++){
            matrix[i][j] += matrix[i][j-1];
        }
    }

    for(int i = l1;i<=l2;i++){
        if(r1!=0){
            sum+= (matrix[i][r2]-matrix[i][r1-1]);
        }else{
            sum+=matrix[i][r2];
        }
        
    }
    for(int i=0;i<=matrix.size();i++){
        for(int j=1;j<=matrix[0].size();j++){
            matrix[i][j] += matrix[i][j-1];
        }
    }
    for(int i=0;i<matrix.size();i++){
        for(int j=0;j<matrix[0].size( );j++){
            cout<<matrix[i][j]<<" ";
        }cout<<endl;
    }


    return sum;
}

int main(){
    int n,m;
    cin>>n>>m;
    vector <vector<int > > matrix(n,vector<int> (m));

    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            cin>>matrix[i][j];
        }
    }

    int l1,r1,l2,r2;
    cout<<"Enter the range of rows and columns to find prefix sum: ";
    cin>>l1>>r1>>l2>>r2;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            cout<<matrix[i][j]<<" ";
        }cout<<endl;
    }

    int sum = rectangleSum(matrix,l1,r1,l2,r2);
    cout<<"Sum: "<<sum<<endl;
    return 0;
}
