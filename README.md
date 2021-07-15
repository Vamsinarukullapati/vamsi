//linear probing using c++
#include <stdio.h>
#include<iostream>
using namespace std;
class LinearPr
{
    private:
          int n;
          int *h;
    public:
            LinearPr(int n)
           {
               this->n=n;
               h=(int*)calloc(n,sizeof(int));
           }
           int hashkey(int data)
           {
               return data%n;
           }
           void insert(int data)
           {
               int j;
               int i=hashkey(data);
               for( j=0;j<n;j++)
               {
                   int k=(i+j)%n;
                   if(h[k]==0)
                   {
                       h[k]=data;
                       break;
                   }
               }
               if(n==j)
               {
                   cout<<"the hash was full"<<endl;
               }
               display();
           }
           int serach(int data)
           {
              int i=hashkey(data);
              for(int j=0;j<n;j++)
              {
                  int k=(i+j)%n;
                  if(h[k]==data)
                   return i;
              }
              return -1;
           }
           
           void remove(int data)
           {
               int i=hashkey(data);
               if(i!=-1)
               {
                   cout<<"the deleted elememt is:"<<h[i]<<endl;
                   h[i]=0;
               }
               else
               cout<<"the element is not found"<<endl;
               display();
           }
           void display()
           {
              for(int i=0;i<n;i++)
              {
                  cout<<"h["<<i<<"] :["<<h[i]<<"]"<<endl;
              }
               
           }
};

int main()
{
    int ch,val,i,n;
    cout<<"entre the table size"<<endl;
    cin>>n;
    
    LinearPr o(n);
    
    
    while(1)
    {cout<<"enter the choice 1.insert 2.remove 3.search"<<endl;
        cin>>ch;
        switch(ch)
        {
            case 1:cout<<"enter the data"<<endl;
                   cin>>val;
                   o.insert(val);
                  break;
            case 2: o.remove(20);
                     break;
            case 3:cout<<"entre the seacrch element:";
                           cin>>val;
                    i=o.serach(val);
                         if(i!=-1)
                          {
                           cout<<"the ele is found at:"<<i<<endl;
    
                            }
                             else
                                 cout<<"not found"<<endl; 
                        break;         
            default:cout<<"invalid choice";
                     exit(0);
                     
                                 
        }
    }
    return 0;
}
    
