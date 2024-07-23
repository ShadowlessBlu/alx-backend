# Pagination

This project contains tasks for learning to paginate data.

## Tasks To Complete

+ [x] 0. **Simple helper function**<br/>[0-simple_helper_function.py](0-simple_helper_function.py) contains a Python function named `index_range` that takes two integer arguments `page` and `page_size` and meets the following requirements:
  + The function should return a tuple of size two containing a start index and an end index corresponding to the range of indexes to return in a list for those particular pagination parameters.
  + Page numbers are 1-indexed, i.e. the first page is page 1.

+ [x] 1. **Simple pagination**<br/>[1-simple_pagination.py](1-simple_pagination.py) contains a Python script that meets the following requirements:
  + Copy `index_range` from the previous task and the following class into your code.
    ```python
    import csv
    import math
    from typing import List


    class Server:
        """Server class to paginate a database of popular baby names.
        """
        DATA_FILE = "Popular_Baby_Names.csv"

        def __init__(self):
            self.__dataset = None

        def dataset(self) -> List[List]:
            """Cached dataset
            """
            if self.__dataset is None:
                with open(self.DATA_FILE) as f:
                    reader = csv.reader(f)
                    dataset = [row for row in reader]
                self.__dataset = dataset[1:]

            return self.__dataset

        def get_page(self, page: int = 1, page_size: int = 10) -> List[List]:
            pass
    ```
  + Implement a method named `get_page` that takes two integer arguments `page` with default value 1 and `page_size` with default value 10.
    + You have to use this [CSV file](Popular_Baby_Names.csv).
    + Use `assert` to verify that both arguments are integers greater than 0.
    + Use `index_range` to find the correct indexes to paginate the dataset correctly and return the appropriate page of the dataset (i.e. the correct list of rows).
    + If the input arguments are out of range for the dataset, an empty list should be returned.

+ [x] 2. **Hypermedia pagination**<br/>[2-hypermedia_pagination.py](2-hypermedia_pagination.py) contains a Python script that meets the following requirements:
  + Replicate code from the previous task.
  + Implement a `get_hyper` method that takes the same arguments (and defaults) as `get_page` and returns a dictionary containing the following key-value pairs:
    + `page_size`: the length of the returned dataset page.
    + `page`: the current page number.
    + `data`: the dataset page (equivalent to the return value from previous task).
    + `next_page`: number of the next page, `None` if no next page.
    + `prev_page`: number of the previous page, `None` if no previous page.
    + `total_pages`: the total number of pages in the dataset as an integer.
  + Make sure to reuse get_page in your implementation.
  + You can use the `math` module if necessary.


## RESOURCES
+ [x] [REST API Design: Pagination](https://intranet.alxswe.com/rltoken/7Kdzi9CH1LdSfNQ4RaJUQw)
+ [x] [HATEOAS](https://intranet.alxswe.com/rltoken/tfzcEbTSdMYSYxsspJH_oA) 
