
# 0x00 Pagination Project

-----

This project focuses on implementing pagination techniques for efficient data retrieval. It includes three main tasks:

1. **Simple Helper Function: `index_range`**
   - Write a function named `index_range` that takes two integer arguments: `page` and `page_size`.
   - The function should return a tuple containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters.
   - Note: Page numbers are 1-indexed, i.e., the first page is page 1.

2. **Simple Pagination: `get_page`**
   - Copy the `index_range` function from the previous task.
   - Implement a method named `get_page` that takes two integer arguments: `page` (default value 1) and `page_size` (default value 10).
   - Use the provided CSV file (e.g., `Popular_Baby_Names.csv`) as your dataset.
   - Verify that both arguments are integers greater than 0 using `assert`.
   - Utilize the `index_range` function to find the correct indexes for pagination and return the appropriate page of the dataset (i.e., the correct list of rows).
   - If the input arguments are out of range for the dataset, return an empty list.

3. **Hypermedia Pagination: `get_hyper`**
   - Replicate the code from the previous task.
   - Implement a method named `get_hyper` that takes the same arguments (and defaults) as `get_page`.
   - Return a dictionary with the following key-value pairs:
     - `page_size`: the length of the returned dataset page
     - `page`: the current page number
     - `data`: the dataset page (equivalent to the return from the previous task)
     - `next_page`: the number of the next page (or `None` if no next page)
     - `prev_page`: the number of the previous page (or `None` if no previous page)
     - `total_pages`: the total number of pages in the dataset as an integer
   - Reuse the `get_page` implementation.
   - You can use the `math` module if necessary.

4. **Deletion-Resilient Hypermedia Pagination: `get_hyper_index`**
   - Implement a method named `get_hyper_index` with two integer arguments: `index` (default value `None`) and `page_size` (default value of 10).
   - Return a dictionary with the following key-value pairs:
     - `index`: the current start index of the return page (index of the first item in the current page)
     - `next_index`: the next index to query with (index of the first item after the last item on the current page)
     - `page_size`: the current page size
     - `data`: the actual page of the dataset
   - Use `assert` to verify that the index is in a valid range.
   - For example, if requesting page 3 with a page size of 20 (and no data was removed from the dataset), the current index should be 60.
   - If the user queries index 0 with page size 10, they will get rows indexed 0 to 9 included.
   - If they request the next index (10) with page size 10, but rows 3, 6, and 7 were deleted, the user should still receive rows indexed 10 to 19 included.
