# .........................sorting patterns .....................

##### problem 1:Sort Integers by The Number of 1 Bits(leetcode,sort) ->  sort the integers in the array in ascending order by the number of 1's in their binary representation and in case of two or more integers have the same number of 1's you have to sort them in ascending order.
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
    
    
##### problem 2:  intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]] ,newInterval = [4,8];; Output: [[1,2],[3,10],[12,16]]
    vector<vector<int>> insert(vector<vector<int>>& intervals, vector<int>& newInterval) {    
    intervals.push_back(newInterval);
    sort(intervals.begin(),intervals.end());
    vector<vector<int>>v;
    v.push_back(intervals[0]);
    for(int i=1; i<intervals.size(); i++)
    {
    vector<int>&curr=v.back();

        if(curr[1]<intervals[i][0])
        {
            v.push_back(intervals[i]);
        }
        else if(curr[1] < intervals[i][1])
        {
            curr[1]=intervals[i][1];
        }
    }    
        return v;               
    }
  ##### Input: [[1,3],[2,6],[8,10],[15,18]] ; Output: [[1,6],[8,10],[15,18]] ;Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        if(intervals.empty() || intervals.size()==1)
                return intervals;
        
        sort(intervals.begin(),intervals.end());
        vector<vector<int>>v;
        v.push_back(intervals[0]);
        for(int i=1; i<intervals.size(); i++){
           vector<int>&curr=v.back();  
            if(curr[1] < intervals[i][0])
                v.push_back(intervals[i]);
           else if(curr[1] < intervals[i][1])
                curr[1]=intervals[i][1];
        }
       return v;
        
    }
##### Given a list of non negative integers, arrange them such that they form the largest number ->[10,2]=[2,10]
         static int cmp(const int &a, const int &b)
        {

    return to_string(a)+to_string(b) > to_string(b)+to_string(a);
        }
     string largestNumber(vector<int>& nums) {
        
    sort(nums.begin(),nums.end(),cmp);
    string a="";
    for(int i=0; i<nums.size(); i++)
    {
    a=a+to_string(nums[i]);
    }
        if(a[0]=='0')
            a="0";
      return a;  
    }
        link :https://www.geeksforgeeks.org/given-an-array-of-numbers-arrange-the-numbers-to-form-the-biggest-number/
