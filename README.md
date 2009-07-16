Overview
=============
add support for multiple values on setf.

this extension re-define some functions in lisp/setf.l to make setf
support multiple values.

- lisp::optimize-setf-method
- lisp::setf-expand-1
- lisp::get-setf-method

and define-setf-method for values.

License
============
The MIT License

Copyright (c) <year> <copyright holders>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


Usage
=======
just put setf-values.l somewhene in *load-path* and load it.

(require "setf-values")


Notes
======

when you need original implementation of setf for some reasons, they
are stored in lisp::+original-<function-name>+. so you can restore
them by eval following.

    ;;; restoring original functions
    (setf (symbol-function lisp::get-setf-method)
          lisp::+original-get-setf-method
          (symbol-function lisp::optimize-setf-method)
          lisp::+original-optimize-setf-method
          (symbol-function lisp::setf-expand-1)
          lisp::+original-setf-expand-1)
