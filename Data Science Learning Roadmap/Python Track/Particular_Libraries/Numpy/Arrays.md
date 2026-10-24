# General
A N-dimensional array object, from NumPy, or _ndarry_, is a "generic multidimensional container for homogeneous data; that is all the elements must be the same type." 

The advantage using NumPy is that you can do quick maths on these, in contrast to a different data type.

The easiest way to create an array  is to use the `array()` function, a method which you use most often on a candidate container of data, like a list. 

You can inspect a ndarry using `ndim()` and `shape`. 
# Array Functions Table
Some important NumPy array creation functions: 

Function Description 

`array` Convert input data (list, tuple, array, or other sequence type) to an ndarray either by inferring a data type or explicitly specifying a data type; copies the input data by default|

`asarray` Convert input to ndarray, but do not copy if the input is already an ndarray

`arange` Like the built-in `range` but returns an ndarray instead of a list|

`ones, ones_like` Produce an array of all 1s with the given shape and data type; `ones_like` takes another array and produces a `ones` array of the same shape and data type|

`zeros, zeros_like` Like `ones` and `ones_like` bu
t producing arrays of 0s instead|

`empty, empty_like` Create new arrays by allocating new memory, but do not populate with any values like `ones` and `zeros`

`full, full_like` Produce an array of the given shape and data type with all values set to the indicated "fill value"; `full_like` takes another array and produces a filled array of the same shape and data type|

`eye, identity` Create a square N × N identity matrix (1s on the diagonal and 0s elsewhere)

You can explicitly convert or _cast_ an array from one data type to another using ndarray’s `astype` method. 

# Arithmetic with NumPy Arrays

Arrays are important because they enable you to express batch operations on data without writing any `for` loops. NumPy users call this _vectorization_. Any arithmetic operations between equal-size arrays apply the operation element-wise,

```
arr = np.array([[1, 2, 3], [4, 5, 6]])

arr * arr == ([[1, 4, 9], [16, 25, 36]]) 

#or

arr - arr == ([[0, 0, 0], [0, 0, 0]]) 
```

Comparing equal-sized arrays can also yield boolean values, element-wise. Evaluating operations between differently sized arrays is called _broadcasting_ and will be discussed in more detail in [Appendix A: Advanced NumPy](https://wesmckinney.com/book/advanced-numpy.html). Having a deep understanding of broadcasting is not necessary for most of this book.

# Basic Indexing and Slicing

One-dimensional arrays act identical to lists when indexing/slicing.

E.g.,

```
arr = np.arange(10)

arr == ([1,2,3,4,5,6,7,8,9])

arr[5] == 5

arr[5:8] = 12

arr == ([1,2,3,4,12,12,12,8,9])
```

An important first distinction from Python's built-in lists is that array slices are _views_ on the original array. This means that the data is not copied, and any modifications to the view will be reflected in the source array.

The "bare" slice `[:]` will assign to all values in an array.

If you want a copy of a slice of an ndarray instead of a view, you will need to explicitly copy the array—for example, `arr[5:8].copy()`. As you will see, pandas works this way, too.

We can index or grab elements of a multi-dimensional array such as:

```
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
arr[0, 2] == 3
#OR
arr[0][2] == 3
```


Indexing on a two-dimensional array, I find it helpful to think of axis 0 as the "rows" of the array and axis 1 as the "columns."
![[Pasted image 20261024150355.png]]
