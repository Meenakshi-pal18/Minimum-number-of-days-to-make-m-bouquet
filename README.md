# Minimum-number-of-days-to-make-m-bouquet
class Solution {
public:
bool canBloom(vector<int>& bloomDay,int mid,int m,int k){
    int cnt=0;
    int cos=0;
    
        for(int x:bloomDay){
        if(x<=mid){
            cnt++;
        }
        else {
            cnt=0;
        }
        if(cnt==k){
            cos++;
            cnt=0;
        }
        }
    return cos>=m;
}
    int minDays(vector<int>& bloomDay, int m, int k) {
        int l=1;
        int r=*max_element(bloomDay.begin(),bloomDay.end());
        int res=-1;
        while(l<=r){
            int mid=l+(r-l)/2;
            if(canBloom(bloomDay,mid,m,k)){
                res=mid;
                r=mid-1;
            }
            else{
                l=mid+1;
            }
        }
        return res;
    }
};
