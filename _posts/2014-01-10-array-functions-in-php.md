---
title: Array functions in PHP
author: sarathlal
layout: post
tags:
  - PHP
---
When we begin PHP programming, often we want to deal with arrays. In default, PHP have an interesting list of array functions.

If we are not familiar with these default functions, we tend to build our own scrappy codes instead of using these functions.

So to familiarize with available array functions in PHP, I just list all of them here with a small description & link to PHP manual.

*   [array\_change\_key_case][1]  
    &mdash; Changes the case of all keys in an array 
*   [array_chunk][2]  
    &mdash; Split an array into chunks 
*   [array_column][3]  
    &mdash; Return the values from a single column in the input array 
*   [array_combine][4]  
    &mdash; Creates an array by using one array for keys and another for its  
    values 
*   [array\_count\_values][5]  
    &mdash; Counts all the values of an array 
*   [array\_diff\_assoc][6]  
    &mdash; Computes the difference of arrays with additional index check 
*   [array\_diff\_key][7]  
    &mdash; Computes the difference of arrays using keys for comparison 
*   [array\_diff\_uassoc][8]  
    &mdash; Computes the difference of arrays with additional index check  
    which is performed by a user supplied callback function 
*   [array\_diff\_ukey][9]  
    &mdash; Computes the difference of arrays using a callback function on  
    the keys for comparison 
*   [array_diff][10]  
    &mdash; Computes the difference of arrays 
*   [array\_fill\_keys][11]  
    &mdash; Fill an array with values, specifying keys 
*   [array_fill][12]  
    &mdash; Fill an array with values 
*   [array_filter][13]  
    &mdash; Filters elements of an array using a callback function 
*   [array_flip][14]  
    &mdash; Exchanges all keys with their associated values in an array 
*   [array\_intersect\_assoc][15]  
    &mdash; Computes the intersection of arrays with additional index check 
*   [array\_intersect\_key][16]  
    &mdash; Computes the intersection of arrays using keys for comparison 
*   [array\_intersect\_uassoc][17]  
    &mdash; Computes the intersection of arrays with additional index check,  
    compares indexes by a callback function 
*   [array\_intersect\_ukey][18]  
    &mdash; Computes the intersection of arrays using a callback function on  
    the keys for comparison 
*   [array_intersect][19]  
    &mdash; Computes the intersection of arrays 
*   [array\_key\_exists][20]  
    &mdash; Checks if the given key or index exists in the array 
*   [array_keys][21]  
    &mdash; Return all the keys or a subset of the keys of an array 
*   [array_map][22]  
    &mdash; Applies the callback to the elements of the given arrays 
*   [array\_merge\_recursive][23]  
    &mdash; Merge two or more arrays recursively 
*   [array_merge][24]  
    &mdash; Merge one or more arrays 
*   [array_multisort][25]  
    &mdash; Sort multiple or multi-dimensional arrays 
*   [array_pad][26]  
    &mdash; Pad array to the specified length with a value 
*   [array_pop][27]  
    &mdash; Pop the element off the end of array 
*   [array_product][28]  
    &mdash; Calculate the product of values in an array 
*   [array_push][29]  
    &mdash; Push one or more elements onto the end of array 
*   [array_rand][30]  
    &mdash; Pick one or more random entries out of an array 
*   [array_reduce][31]  
    &mdash; Iteratively reduce the array to a single value using a callback  
    function 
*   [array\_replace\_recursive][32]  
    &mdash; Replaces elements from passed arrays into the first array  
    recursively 
*   [array_replace][33]  
    &mdash; Replaces elements from passed arrays into the first array 
*   [array_reverse][34]  
    &mdash; Return an array with elements in reverse order 
*   [array_search][35]  
    &mdash; Searches the array for a given value and returns the  
    corresponding key if successful 
*   [array_shift][36]  
    &mdash; Shift an element off the beginning of array 
*   [array_slice][37]  
    &mdash; Extract a slice of the array 
*   [array_splice][38]  
    &mdash; Remove a portion of the array and replace it with something else 
*   [array_sum][39]  
    &mdash; Calculate the sum of values in an array 
*   [array\_udiff\_assoc][40]  
    &mdash; Computes the difference of arrays with additional index check,  
    compares data by a callback function 
*   [array\_udiff\_uassoc][41]  
    &mdash; Computes the difference of arrays with additional index check,  
    compares data and indexes by a callback function 
*   [array_udiff][42]  
    &mdash; Computes the difference of arrays by using a callback function  
    for data comparison 
*   [array\_uintersect\_assoc][43]  
    &mdash; Computes the intersection of arrays with additional index check,  
    compares data by a callback function 
*   [array\_uintersect\_uassoc][44]  
    &mdash; Computes the intersection of arrays with additional index check,  
    compares data and indexes by a callback functions 
*   [array_uintersect][45]  
    &mdash; Computes the intersection of arrays, compares data by a callback  
    function 
*   [array_unique][46]  
    &mdash; Removes duplicate values from an array 
*   [array_unshift][47]  
    &mdash; Prepend one or more elements to the beginning of an array 
*   [array_values][48]  
    &mdash; Return all the values of an array 
*   [array\_walk\_recursive][49]  
    &mdash; Apply a user function recursively to every member of an array 
*   [array_walk][50]  
    &mdash; Apply a user function to every member of an array 
*   [array][51]  
    &mdash; Create an array 
*   [arsort][52]  
    &mdash; Sort an array in reverse order and maintain index association 
*   [asort][53]  
    &mdash; Sort an array and maintain index association 
*   [compact][54]  
    &mdash; Create array containing variables and their values 
*   [count][55]  
    &mdash; Count all elements in an array, or something in an object 
*   [current][56]  
    &mdash; Return the current element in an array 
*   [each][57]  
    &mdash; Return the current key and value pair from an array and advance  
    the array cursor 
*   [end][58]  
    &mdash; Set the internal pointer of an array to its last element 
*   [extract][59]  
    &mdash; Import variables into the current symbol table from an array 
*   [in_array][60]  
    &mdash; Checks if a value exists in an array 
*   [key_exists][61]  
    &mdash; Alias of array\_key\_exists 
*   [key][62]  
    &mdash; Fetch a key from an array 
*   [krsort][63]  
    &mdash; Sort an array by key in reverse order 
*   [ksort][64]  
    &mdash; Sort an array by key 
*   [list][65]  
    &mdash; Assign variables as if they were an array 
*   [natcasesort][66]  
    &mdash; Sort an array using a case insensitive &#8220;natural order&#8221;  
    algorithm 
*   [natsort][67]  
    &mdash; Sort an array using a &#8220;natural order&#8221; algorithm 
*   [next][68]  
    &mdash; Advance the internal array pointer of an array 
*   [pos][69]  
    &mdash; Alias of current 
*   [prev][70]  
    &mdash; Rewind the internal array pointer 
*   [range][71]  
    &mdash; Create an array containing a range of elements 
*   [reset][72]  
    &mdash; Set the internal pointer of an array to its first element 
*   [rsort][73]  
    &mdash; Sort an array in reverse order 
*   [shuffle][74]  
    &mdash; Shuffle an array 
*   [sizeof][75]  
    &mdash; Alias of count 
*   [sort][76]  
    &mdash; Sort an array 
*   [uasort][77]  
    &mdash; Sort an array with a user-defined comparison function and  
    maintain index association 
*   [uksort][78]  
    &mdash; Sort an array by keys using a user-defined comparison function 
*   [usort][79]  
    &mdash; Sort an array by values using a user-defined comparison function

 [1]: http://www.php.net/manual/en/function.array-change-key-case.php
 [2]: http://www.php.net/manual/en/function.array-chunk.php
 [3]: http://www.php.net/manual/en/function.array-column.php
 [4]: http://www.php.net/manual/en/function.array-combine.php
 [5]: http://www.php.net/manual/en/function.array-count-values.php
 [6]: http://www.php.net/manual/en/function.array-diff-assoc.php
 [7]: http://www.php.net/manual/en/function.array-diff-key.php
 [8]: http://www.php.net/manual/en/function.array-diff-uassoc.php
 [9]: http://www.php.net/manual/en/function.array-diff-ukey.php
 [10]: http://www.php.net/manual/en/function.array-diff.php
 [11]: http://www.php.net/manual/en/function.array-fill-keys.php
 [12]: http://www.php.net/manual/en/function.array-fill.php
 [13]: http://www.php.net/manual/en/function.array-filter.php
 [14]: http://www.php.net/manual/en/function.array-flip.php
 [15]: http://www.php.net/manual/en/function.array-intersect-assoc.php
 [16]: http://www.php.net/manual/en/function.array-intersect-key.php
 [17]: http://www.php.net/manual/en/function.array-intersect-uassoc.php
 [18]: http://www.php.net/manual/en/function.array-intersect-ukey.php
 [19]: http://www.php.net/manual/en/function.array-intersect.php
 [20]: http://www.php.net/manual/en/function.array-key-exists.php
 [21]: http://www.php.net/manual/en/function.array-keys.php
 [22]: http://www.php.net/manual/en/function.array-map.php
 [23]: http://www.php.net/manual/en/function.array-merge-recursive.php
 [24]: http://www.php.net/manual/en/function.array-merge.php
 [25]: http://www.php.net/manual/en/function.array-multisort.php
 [26]: http://www.php.net/manual/en/function.array-pad.php
 [27]: http://www.php.net/manual/en/function.array-pop.php
 [28]: http://www.php.net/manual/en/function.array-product.php
 [29]: http://www.php.net/manual/en/function.array-push.php
 [30]: http://www.php.net/manual/en/function.array-rand.php
 [31]: http://www.php.net/manual/en/function.array-reduce.php
 [32]: http://www.php.net/manual/en/function.array-replace-recursive.php
 [33]: http://www.php.net/manual/en/function.array-replace.php
 [34]: http://www.php.net/manual/en/function.array-reverse.php
 [35]: http://www.php.net/manual/en/function.array-search.php
 [36]: http://www.php.net/manual/en/function.array-shift.php
 [37]: http://www.php.net/manual/en/function.array-slice.php
 [38]: http://www.php.net/manual/en/function.array-splice.php
 [39]: http://www.php.net/manual/en/function.array-sum.php
 [40]: http://www.php.net/manual/en/function.array-udiff-assoc.php
 [41]: http://www.php.net/manual/en/function.array-udiff-uassoc.php
 [42]: http://www.php.net/manual/en/function.array-udiff.php
 [43]: http://www.php.net/manual/en/function.array-uintersect-assoc.php
 [44]: http://www.php.net/manual/en/function.array-uintersect-uassoc.php
 [45]: http://www.php.net/manual/en/function.array-uintersect.php
 [46]: http://www.php.net/manual/en/function.array-unique.php
 [47]: http://www.php.net/manual/en/function.array-unshift.php
 [48]: http://www.php.net/manual/en/function.array-values.php
 [49]: http://www.php.net/manual/en/function.array-walk-recursive.php
 [50]: http://www.php.net/manual/en/function.array-walk.php
 [51]: http://www.php.net/manual/en/function.array.php
 [52]: http://www.php.net/manual/en/function.arsort.php
 [53]: http://www.php.net/manual/en/function.asort.php
 [54]: http://www.php.net/manual/en/function.compact.php
 [55]: http://www.php.net/manual/en/function.count.php
 [56]: http://www.php.net/manual/en/function.current.php
 [57]: http://www.php.net/manual/en/function.each.php
 [58]: http://www.php.net/manual/en/function.end.php
 [59]: http://www.php.net/manual/en/function.extract.php
 [60]: http://www.php.net/manual/en/function.in-array.php
 [61]: http://www.php.net/manual/en/function.key-exists.php
 [62]: http://www.php.net/manual/en/function.key.php
 [63]: http://www.php.net/manual/en/function.krsort.php
 [64]: http://www.php.net/manual/en/function.ksort.php
 [65]: http://www.php.net/manual/en/function.list.php
 [66]: http://www.php.net/manual/en/function.natcasesort.php
 [67]: http://www.php.net/manual/en/function.natsort.php
 [68]: http://www.php.net/manual/en/function.next.php
 [69]: http://www.php.net/manual/en/function.pos.php
 [70]: http://www.php.net/manual/en/function.prev.php
 [71]: http://www.php.net/manual/en/function.range.php
 [72]: http://www.php.net/manual/en/function.reset.php
 [73]: http://www.php.net/manual/en/function.rsort.php
 [74]: http://www.php.net/manual/en/function.shuffle.php
 [75]: http://www.php.net/manual/en/function.sizeof.php
 [76]: http://www.php.net/manual/en/function.sort.php
 [77]: http://www.php.net/manual/en/function.uasort.php
 [78]: http://www.php.net/manual/en/function.uksort.php
 [79]: http://www.php.net/manual/en/function.usort.php
