# Search-in-Rotated-Sorted-Array

int search(vector<int>& nums, int target) {
        int pivot = getPivot(nums, target);
        cout<<pivot<<endl;
        if(nums[pivot] == target)
            return pivot;
        if(target>=nums[pivot] && target<=nums[nums.size()-1]){
            return bin(nums, pivot, nums.size()-1, target);
        }
        else{
            return bin(nums, 0, pivot, target);
        }
    }

    int getPivot(vector<int>& nums, int target){
        int mid;
        int s=0;
        int e=nums.size()-1;

        while(s<e){
            mid = (s+e)/2;

            if(nums[mid]>=nums[0]){
                s=mid+1;
            }
            else{
                e=mid;
            }
        }
        return s;
    }

    int bin(vector<int>& nums, int s, int e, int target){
        int mid;

        while(s<=e){
            mid = (s+e)/2;

            if(nums[mid] == target){
                return mid;
            }
            else if(target>nums[mid]){
                s = mid+1;
            }
            else{
                e = mid-1;
            }
        }
        return -1;
    }
