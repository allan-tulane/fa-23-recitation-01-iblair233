[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11681057&assignment_repo_type=AssignmentRepo)
# CMPS 2200  Recitation 01

**Name (Team Member 1):**Izzy Blair  
**Name (Team Member 2):**Ethan Schaferkotter

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 
For both linear and binary search, the worst case input is a key that is not in the list to search. For example, in a list of 1,2,3,4,5, the worse case input is six for both.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 
The best ccase input values are those keys that are found first. For example, with a list that goes 1,2,3,4,5: the best case for linear search is 1, and for binary it is 3.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.003 |    0.002 |
|      100 |    0.006 |    0.001 |
|     1000 |    0.066 |    0.001 |
|    10000 |    0.802 |    0.003 |
|   100000 |    6.761 |    0.007 |
|  1000000 |  107.207 |    0.007 |
| 10000000 | 1474.503 |    0.006 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

They do not match all of my empirical results. For the linear search, they match pretty well because as n grows, the time grows with it. However, the binary search times do not quite grow the way we would expect it to -- the times remain pretty much the same. I think this is because the hardware I am using makes the binary search much more efficient than we would expect.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? for linear search, the time complexity it Theta(k*n^2)
  + For binary search? Theta(n^2) + Theta(k*log2(n))
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? Because the Theta(n^2) will become increasingly larger as k increases, linear search without sorting would be more efficient for large numbers of k. Smaller values of k will be more efficient with sorted binary search.