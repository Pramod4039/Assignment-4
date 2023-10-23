# Assignment-4:
1: Top k frequent elements: 
    Algorithm used: 
        'collections.Counter(nums)' is used to count the occurrences of each element in the nums array, resulting in a dictionary-like object where keys are the unique elements in nums, and values are their frequencies.
        To keep the k most frequent components, a max-heap (heap) is built. The negative frequencies are implemented as a min-heap, which is why the tuple contains the string "-freq." The min-heap effectively becomes a max-heap when negative values are used, reversing the order of the items.
        The list 'heap' is converted into a legitimate heap structure using the function 'heapq.heapify(heap)'.
        The k most frequent elements are placed at the beginning of a result list.
        The loop for _ in range(k) repeatedly pops the element with the highest (most negative) frequency and adds the associated element (the second element in the tuple) to the result list in order to extract the k most frequent elements from the max-heap.
        The k most frequent elements in the result list are returned.
    Time complexity:
        Using collections to count how many times each element appears.The length of Counter is O(n), where n is the size of the input array nums.
        Since the heap has a maximum of k elements and each insertion into the heap requires O(log(n)) time, it takes O(k * log(n)) time to create the heap of distinct elements with their negative frequencies.
        It takes O(k * log(k)) time to extract the k most frequent entries from the heap.
        In the worst situation, this algorithm's temporal complexity is O(n + k * log(n)). If k is less than log(n), it can roughly be expressed as O(n). Because we only remove one element from the heap in the second example with k = 1, the time complexity is O(n).

2: Find k closest elements:
    Algorithm used:
        Create two pointers, left and right, and initialize them to keep a window with k items. Right is initially at the end of the array (index len(arr) - 1) and left is initially at the beginning of the array (index 0).
        Utilize a while loop to iteratively reduce the window's size until it contains exactly k elements. As long as the gap between the right and left is larger than or equal to k, the loop will keep going.
        Compare the absolute differences between the elements to the left and right of the target value x inside the loop. The element that is nearer to x has a lower absolute difference. Increase the left pointer if the left element is closer; decrease the right pointer otherwise.
        The k nearest elements are found in the window specified by left and right when the loop ends.
        As a result, return the window's contents.
    Time Complexity:
        This approach has an O(log(n) + k) time complexity, where n is the length of the input array arr. The window is expanded to include k additional elements once the initial binary search phase, which finds the element that is closest to the input x in O(log(n)) time, has been completed. Since k is the maximum number of components we desire in the result, the window expansion step runs in the worst case in O(k) time. As desired, the overall time complexity is therefore better than O(n log(n)).

3: K largest elements of Max Heap:
    Algorithm used: 
        max_heap, k, findTopKElements Algorithm:
        To store the top k entries, create the empty list top_k.
        Use the loop variable i to iterate across the range from 0 to k (exclusively).
        Within the loop
            a. Verify that i is within the constraints of the array by seeing if it is shorter than the max_heap.
            b. If the criterion is satisfied, add the element from the max_heap at index i to the top_k list.
            c. To make sure the max heap property is kept for the max_heap, call the max_heapify function.
            d. Exit the loop if the step 3a requirement is not satisfied (i.e., there are still more than k elements in the heap).
        Give back the top_k list, which contains the first k elements.
        size, index, and max_heapify (max_heap) Algorithm:
        Start with the largest element, the index index.
        Determine the indices of the current node's left (left_child) and right (right_child) children:
        left_child = 2 * index + 1
        right_child = 2 * index + 2
        Update largest to be the index of the left_child if the left_child exists and is larger than the element at the largest index.
        Update largest to be the index of the right_child if the right_child is present and greater than the element at the largest index.
        To maintain the max heap property, swap the elements at the index and largest indices in the max_heap if the largest index is not equal to the original index.
        To guarantee that the max heap property is maintained in the subtree, call max_heapify recursively on the greatest index.
    Time Complexity:
        The findTopKElements method performs its main loop k times.
        The max_heapify function, whose time complexity is O(log n), where n is the size of the heap, is used once throughout each iteration.
        As a result, the findTopKElements function's time complexity is O(k * log n), where n is the heap's size.
        Overall, the algorithm effectively preserves the original heap structure while finding the top k elements from the maximum heap.

4: Shortest subarray with sum atleat K:
    Algorithm used:
        In order to hold the cumulative sums of the input array nums, create the prefix sum array prefix_sum with an additional member.
        Make a deque called deque_window and set min_subarray_length's initial value to a positive integer of infinity.
        Prefix sums should be calculated and stored in prefix_sum when you iterate through the input array nums.
        Perform the following for each index i from 0 to length:
            Update min_subarray_length by taking the minimum between the current value of min_subarray_length and the difference of i and the front element of deque_window as long as deque_window is not empty and the difference between the current prefix sum prefix_sum[i] and the prefix sum at the front of deque_window is greater than or equal to k. From deque_window, eliminate the front element.
            Remove the back element from deque_window while deque_window is not empty and the prefix sum at index i is less than or equal to the prefix sum at the back of deque_window.
            To deque_window, append the current index, i.
        If min_subarray_length is not positive infinity, it should be returned as a valid subarray length. If not, return -1.
    Time complexity:
        This code has an O(n) time complexity, where n is the size of the input array nums. The array is iterated through once to compute the prefix sums and once more to determine the shortest subarray length. The deque's internal operations (popleft and pop), which typically take constant time, have no impact on the time complexity as a whole. As a result, the time complexity of the code is proportional to the size of the input.

5: Kth Smallest Prime Fraction:
    Algorithm used: 
        Make the left and right initial values. These depict the many fractional values that might range from 0 to 1.
        While left is less than right, enter a binary search loop.
        As the average of left and right, calculate mid. This displays the percent that is currently being considered.
        Set up the count and maximumFraction to one. Both count and maxFraction keep track of the total number of fractions detected that are less than or equal to mid.
        Set the value of an index j to 0.
        Go over the arr array repeatedly.
            Increase j even though j is shorter than arr[i] and arr[i] is greater than mid * arr[j]. Making sure you're counting fractions less than mid is ensured by this step.
            The amount of elements left in arr (len(arr) - j) should be added to the count because they are still valid fractions.
            By choosing the highest value between the existing maxFraction and the ratio arr[i]/arr[j], update maxFraction.
        Verify whether count is smaller than k. If so, move the slider from left to middle to indicate that you should look in a higher range.
        If not, adjust right to mid, which signifies that you should look in a lower range.
        Till left and right are very near together, repeat the binary search cycle.
        Array [arr[0], maxFraction] should include the final fraction.
    Time complexity:
        This algorithm's time complexity is O(n * log(max_value)), where
            The length of the array, arr, is n.
            The arr array's maximum value is represented by max_value.
        The loop in the binary search process runs in O(log(max_value)) iterations until left and right are very close to one another. You traverse the arr array in each iteration, which takes O(n) time. The total time complexity is therefore O(n * log(max_value)).

