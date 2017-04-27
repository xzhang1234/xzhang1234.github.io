   
#### Summary:
1. Invariant  
2. Make progress in each iteration   
3. Properties after ```while``` loop   


```
1. public int binarySearch(int[] nums, int target) {  
2.        if (nums == null || nums.length == 0) return -1;
3.        int start = 0, end = nums.length - 1;
4.        while (start <= end) {
5.            int mid = start + (end - start)/2;
6.            if (nums[mid] == target) {
7.            		return mid;
8.            } 
9.            if (nums[mid] > target) {
10.                end = mid - 1;
11.           } else {
12.                start = mid + 1;
13.           }
14.        }
15.        return -1;
16. }
```

##### 1. Invariant: 
The first interesting part of binary search is (i) line 3: the initialization of ```start``` and ```end```, (ii) line 9-13: the update of ```start``` and ```end```, (iii) line 4: termination criteria tie together. This is mainly due to the code invariant.

Let us see why they tie together.  
1. Line 3 and Line 9-13. Whichever statement is correct here should be kept correct after an iteration. For example, if the target is in [start, end] at line 3, then after an iteration, the target should be in [start, end] as well. Therefore, line 3 and line 9-13 tie together.  
2. Line 9-13 and Line 4. Since after each iteration, [start, end] includes the target, as long as there is an element in [start, end], we should continue.  

##### 2. Make progress in each iteration:
The second interesting part of binary search is it should make progress in each iteration. Making progress means either ```start``` increases or ```end``` decreases in an iteration. 
This is very important since otherwise you will never end with an infinite loop.

Let us see why the above code will make progress in each iteration.  
1. Since ```start <= end``` in each iteration, ```mid = start + (end - start)/2 >= start``` and ```mid <= end```.  
2. If ```end = mid - 1```, then ```end``` will move to the left at least one position.  
3. If ```start = mid + 1```, then ```start``` will move to the right at least one position.  

Actually, there is another tie here, that is Line 4, Line 5, Line 10 and 12.

##### 3. Properties after the ```while``` loop

Now let us investigate some important properties after jumping out of the ```while``` loop.  
1. ```end = start - 1```.  
2. Three conditions may happen:  
	(i) ```end = -1, start = 0```, which indicates ```nums[end + 1] > target```, i.e., all elements in ```nums``` are larger than ```target```.  
	(ii) ```end = num.length - 1, start = num.length```, which indicates ```nums[start - 1] < target```, i.e., all elements in ```nums``` are smaller than ```target```.  
	(iii) normal condition, ```0 <= end < start <= num.length - 1```, which indicates ```nums[end + 1] > target``` and ```nums[start - 1] < target```. 
