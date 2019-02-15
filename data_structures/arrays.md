# Arrays
## Declaring and Initializing Arrays
An array holds several elements of the same type. It is declared by adding `[]` after the element type:
```java
int[] arr;
```
To initialize an array, you have to use the keyword `new` and specify how many elements the array contains:
```java
arr = new int[4];
```
While the distinction is irrelevant in *most* situations, it's best to think of the array variable as holding a *reference to* the array:

![A box labeled arr, containing an arrow pointing to a row of four boxes each containing a zero](array.svg)

Note that all of the elements of the array are initialized to default values: 0 for numeric types, `false` for booleans, and `null` for reference types (objects and arrays).

If you have a small array and know the specific values you would like it to contain, you can initialize them directly:
```java
String[] names = new String[] {"Akiko", "Bob", "Carlos", "Danielle"};
```
If the declaration and initialization happen on the same line, as in the example above, you are allowed to omit `new String[]`.
## Indexing
Array elements are numbered *starting at 0*. Thus, `arr[0]` is the first element of `arr`, `arr[1]` is the second, and so on.

You can use this to access or change any element of an array. If we take our array above and
```java
arr[2] = 8;
```
then the array looks like this:

![The third box now contains an 8 instead of a 0](array_modified.svg)

Java arrays (unlike C arrays) know how long they are. The length of `arr` is `arr.length`.

## Multidimensional Arrays
## Additional Resources
### Online
### Print
## Questions
1. :star: Can an array have length 0?
1. :star: What is the index of the *last* element of an array `arr`?
## Answers
1. Yes, 0 is a valid length.
1. `arr.length - 1`. This is because indices start at 0; if there are 10 elements, they are numbered 0 through 9.
