# .........................sorting patterns .....................

##### problem:Sort Integers by The Number of 1 Bits(leetcode,sort) ->  sort the integers in the array in ascending order by the number of 1's in their binary representation and in case of two or more integers have the same number of 1's you have to sort them in ascending order.
        static int bin(int n)
    {
       long long int x=0,i=1;
        while(n!=0)
        {
            x=x+n%2;
            n=n/2;
            i=i*10;
        }
    return x;    
    }


      static bool cmp(int a, int b)
    {
        int x=a;
        int y=b;
        a=bin(a);
        b=bin(b);
        if(a<b)
            return true;
        if(a==b)
        {
            if(x<y)
                return true;
            return false;
        }
        return false;
    }
    
    vector<int> sortByBits(vector<int>& arr) {
         stable_sort(arr.begin(),arr.end(),cmp);
            return arr;       
    }
