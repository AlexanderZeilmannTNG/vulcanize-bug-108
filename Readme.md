This is a minimal example
=========================


for the the vulcanize bug [108](http://github.com/polymer/vulcanize/issues/108).

It demonstrates the problem that vulcanize does not work if the paths are given as absolute paths.


What is going on?
-----------------

The ```absolute``` and the ```relative``` folder contain exactly the same code, except in ```absolute``` all paths are absolute and in ```relative``` all are relative.

Vulcanizing the relative folder will work as expected.
Vulcanizing the absolute folder will **not** work as expected. Problems:

* The JavaScript files are not concatenated.
* An empty script file (absolute.js) is created.
* The html of the web components is not inlined.
* In fact the only changes in the html file are:
	* a reference to the absolute.js file.
	* some line breaks changed


Commands
--------

The commands used for the vulcanization are:

```
vulcanize -o absolute.html --csp --inline absolute/index.html
```
and

```
vulcanize -o relative.html --csp --inline relative/index.html
```
