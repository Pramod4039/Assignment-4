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