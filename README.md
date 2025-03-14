
<!--#echo json="package.json" key="name" underline="=" -->
natcmp-deluxe-pmb
=================
<!--/#echo -->

<!--#echo json="package.json" key="description" -->
A natural compare function to make your `.sort()` sort numbers numerically,
with advanced bells and whistles (multi-dimensional, sign-aware for actual
numbers, …).
<!--/#echo -->



API
---

* ⚠ Vaporware ⚠

This module exports one function:

### natcmp(opt)

Return a function that will compare two items and return a number compatible
with JavaScript Array's `.sort()` method.

* Side note: Remember that since 0 means "no preference", you can chain
  multiple comparison functions using the `||` operator.


`opt` is an optional options object that supports these optional keys:

* (If instead `opt` is an array, it will be treated as the `fields` option.)
* `fields`: If false-y (default), treat each input item as one single field.
  Otherwise, it's expected to be Array-like (with `.length` and numbered
  entries) list of field names to sort by.
  The field names are converted to strings, and then treated as key names
  for top-level properties of your input objects.
  For your convenience, if the key name starts with `+` (U+002B plus sign)
  or `-`(U+002D hyphen-minus), they are treated as hints to sort
  ascending and descending. This makes it so when you sort an array of arrays
  and want to inversely sort by the 3rd column, you can just specify
  `fields: [-2]`; however, when you sort an array of objects that actually
  have a property literally named `'-2'` and want to sort them ascending,
  you need to specify it as `fields: ['+-2']`.
* `lower`: (default: `false`) When comparing strings, whether to convert both
  of them to lower case first. Note that doing this in each comparison is
  usually a waste of resources. See below for better solutions.
* `invert`: (default: `false`) Whether to invert all comparisons.
  This will apply separate from the potential hyphen-minus in a field name,
  making those become double inversions.



:TODO: Draft .prep and/or .sort to help with preparation steps.
We can summarize/transform/optimize the original items if necessary,
then sort a list of array indices (originally 0..(n-1)) by the properties
of the original items or of the summary items, then use the sorted indices
to reassemble the original data.





Usage
-----

:TODO:
see [test/usage.mjs](test/usage.mjs).



<!--#toc stop="scan" -->



Known issues
------------

* Vaporware.
* Needs more/better tests and docs.




&nbsp;


License
-------
<!--#echo json="package.json" key="license" -->
ISC
<!--/#echo -->
