
# Important Topic :- 

 - [Bit Manipulation](https://github.com/adityas-ops/bit-manipulation/blob/main/README.md)
 - [Recursion](https://github.com/adityas-ops/recursion)
 - [Subset]()
 - [Sorting](https://github.com/adityas-ops/bit-manipulation/blob/main/README.md)
 - [Vector](https://github.com/adityas-ops/bit-manipulation/blob/main/README.md)
 - [Set](https://github.com/adityas-ops/bit-manipulation/blob/main/README.md)
 - [Map](https://github.com/adityas-ops/bit-manipulation/blob/main/README.md)
 - [Generating Subset]()
 - [Generating permutaion]()
 

#### Use of Modulo 
In competitive programming there are very use of Modulo due to this we can print a large number .
there are some formula of modulo ( **10^9+7** )

(a+b)%M = ((a%M) + (b%M))%M
(a*b)%M = ((a%M) * (b%M))%M
(a-b)%M = ((a%M)-(b%M) + M)%M
(a/b)%M = ((a%M)*(b^-1)%M)%M  b^-1 is a multiplication inverse

let 10^9+7 = M then what is significant :
1. it is very close to integer rough range 10^9
2. it is prime number so we can find multiplication inverse due to this number .

There are some code to understand Modulo
```c++
// print modulo
#include <bits/stdc++.h>
using namespace std;
#define M 1e9+7
#define int long long
#define float double
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define pi pair<int, int>
#define fast ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
//goldminati



int32_t main(){
fast

int n;
cin>>n;

long long  fact = 1;
for(int i = 2; i<=n;i++)
{
    fact = (fact*i)%M;
}
cout<<fact<<endl;




return 0;
}


```

### Pre - Computation technique

pre compuataion techinque  means already compute some data before entering in test cases.
it is technuque to optimize the code.

We can see above the above code for example ..
**Que :-** let 
t = 1e5
                 n = 1e5
M  = 1e9+7

Where t is test case .
n is number of intergers
M is modulo

```c++
#include <bits/stdc++.h>
using namespace std;
#define int long long
#define float double
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define pi pair<int, int>

#define fast ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
//goldminati

const int M = 1e9+7;

int32_t main(){
fast


int t=1;
cin>>t;
while(t--){
int n;
cin>>n;

int   fact = 1;
for(int i = 2; i<=n;i++)
{
    fact =((fact*i)%M);
}
cout<<fact<<endl;
}


return 0;
}

```

This code's time complexity is O(t * n ) wrost case is n*n.
It means We cannot perform this code only 1 second.

So we can optimize the code 
we can take a array which indexes carry it's factorial

```c++
#include <bits/stdc++.h>
using namespace std;
#define int long long
#define float double
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define pi pair<int, int>
#define fast ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
//goldminati
const int N = 1e9+10;
// const int M = 1e9+7;

int fact[N];

int32_t main(){
fast

fact[0] = fact[1] = 1;
for(int i = 2; i<N;i++){
    fact[i] = fact[i-1]*i;
}

int t=1;
cin>>t;
while(t--){
int n;
cin>>n;
cout<<fact[n]<<endl;
}


return 0;
}

```

### Hashing

Hashing is a technique or process of mapping keys, values into the hash table by using a hash function. It is done for faster access to elements. The efficiency of mapping depends on the efficiency of the hash function used.

Example :
find count of given number for n   qeuries

```c++
// find count of given integer
#include <bits/stdc++.h>
using namespace std;
#define int long long
#define float double
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define pi pair<int, int>
#define fast ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
//goldminati


int32_t main(){
fast
int n;
cin>>n;

int arr[n];
for(int i = 0; i<n;i++){
    cin>>arr[i];
}

int t=1;
cin>>t;
while(t--){
int ct = 0;
int x;
cin>>x;
for(int i = 0 ; i<n; i++){
    if(arr[i] == x){
        ct++;
    }

}
cout<<ct<<endl;
}


return 0;
}


```

This code is also take a n*n time . so this code is also not complete under 1 second.

Now we are using hashing 
firstly we create a array this is called Hash Array and store count of it's indexes

let given array element is : { 3, 5, 5, 7, 7, 8}


| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 
| --- | --- | ---- | ---- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 1 | 0 | 5 | 0 | 2 | 1 |


first row is the index and second row is how many times repeat index.

```c++
// find count of given integer
#include <bits/stdc++.h>
using namespace std;
#define int long long
#define float double
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define pi pair<int, int>
#define fast ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
//goldminati


const int N = 1e7+10;
int has[N];
int32_t main(){
fast
int n;
cin>>n;

int arr[n];
for(int i = 0; i<n;i++){
    cin>>arr[i];
    has[arr[i]]++;
}

int t=1;
cin>>t;
while(t--){
int x;
cin>>x;
cout<<has[x]<<endl;

}


return 0;
}

```



### Level Traversing in binary tree

When we traversal in binary tree using level , left to right then it's called **Level Traversing in binary tree.**


```c++
  vector<vector<int>> ans;
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(root == NULL) return ans;
        
        queue<TreeNode*> q;
        q.push(root);
        
        while(!q.empty()){
            int size = q.size();
            vector<int> level;
            
            for(int i = 0; i< size;i++){
                TreeNode * node = q.front();
                q.pop();
                
                if(node ->left != NULL) q.push(node->left);
                if(node ->right != NULL) q.push(node->right);
                level.push_back(node->val);
            }
            ans.push_back(level);
        }
        return ans;
    }

```
