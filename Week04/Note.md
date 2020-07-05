  使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方
  
    public int findMin(int[] nums) {
        int left=0,right=nums.length-1,mid=0;
        while(left<right){
        
            mid=(left+right)/2;
            if(nums[mid]>nums[right])
                left=mid+1;
            else
                right=mid;
        }
        return left;

    }
     
  和作业里find-minimum-in-rotated-sorted-array那题一样，如果mid对应值 > right对应值，则以mid+1为左边界的右半区域找，否则在以mid为右边界的左半区域找。当left和right重合时，重合位置即为无序的地方
