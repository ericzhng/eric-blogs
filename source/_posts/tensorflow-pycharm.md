---
title: 'How to set up tensorflow in PyCharm in Windows?'
date: 2018-09-18
banner: /eric-blogs/gallery/guitarist.jpg
thumbnail: /eric-blogs/images/tensorflow.jpg
categories:
- Software
- Python
tags:
  - Windows
  - PyCharm
  - Tensorflow
---

In this blog, I would like to show you how to set up tensorflow in PyCharm in Window.

<!--more-->

# Major steps

* Download PyCharm community edition from [PyCharm website](https://www.jetbrains.com/pycharm/download/#section=windows) and install it in Windows 10.

* Download and install Anaconda from [Anaconda website](https://www.anaconda.com/download/#windows).

* Open PyCharm, click Create New Project, give the folder a name in Location, select Existing interpreter of python.exe in Anaconda3 folder, and click OK.

* Go to File->Settings->Project:[your project name]->Project Interpreter, you can choose different interpreters you installed before, or create new interpreter as conda virtual environment.

* Click '+' to install new packages: tensorflow, opencv, etc.

* Go back to the editor, once you are done installing the packages, right click on the project, New->Python File, naming it as test.py.

* Put following code in test.py file, and run the test. If it passes, then the installation is successful. Otherwise there might be some errors.
  - `import tensorflow as tf' 'print(tf.__version__)`


# Some common errors

## Error 1
 * When executing step 7, you may came across errors like the following:
   - Error Messages:
	"Traceback (most recent call last):
	File "C:\Users\Hui Zhang\AppData\Local\Programs\Python\Python35\lib\site-packages\tensorflow\python\pywrap_tensorflow.py", line 58, in <module> from tensorflow.python.pywrap_tensorflow_internal import *
	File "C:\Users\Hui Zhang\AppData\Local\Programs\Python\Python35\lib\site-packages\tensorflow\python\pywrap_tensorflow_internal.py", line 28, in <module> _pywrap_tensorflow_internal = swig_import_helper()	
	File "C:\Users\Hui Zhang\AppData\Local\Programs\Python\Python35\lib\site-packages\tensorflow\python\pywrap_tensorflow_internal.py", line 24, in swig_import_helper_mod = imp.load_module('_pywrap_tensorflow_internal', fp, pathname, description)	
	File "C:\Users\Hui Zhang\AppData\Local\Programs\Python\Python35\lib\imp.py", line 242, in load_module return load_dynamic(name, filename, file)
	File "C:\Users\Hui Zhang\AppData\Local\Programs\Python\Python35\lib\imp.py", line 342, in load_dynamic return _load(spec)	
	ImportError: DLL load failed: A dynamic link library (DLL) initialization routine failed."

 * Solution
   * It is because old CPU doesn't support AVX, and you need to install using the source code of tensorflow. You need to follow [3] to install tensorflow from source file.


Reference:
------
* [1] [Check SSE/AVX instruction support](https://gist.github.com/hi2p-perim/7855506#file-ssecheck-cpp)
* [2] [Issues of installing tensorflow with DLL error](https://github.com/tensorflow/tensorflow/issues/17761)
* [3] [Build from source on Windows](https://www.tensorflow.org/install/source_windows)