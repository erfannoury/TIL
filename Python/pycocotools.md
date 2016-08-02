Python API for MS COCO can't be compiled for Windows out-of-the-box. However, fortunately to the rescue, someone found the changes needed to compile these tools successfully in Windows. You have to change few files (in fact, 3) and then you can compile them API.

The changes are [here](https://github.com/pdollar/coco/compare/master...willyd:windows?expand=1). Thank you [Guillaume Dumont](https://github.com/willyd)!

However, there have been changes in the main repo since when @willyd proposed these changes. So I'll just summarize them here, just in case.

1. Rename `common/maskApi.c` to `common/maskApi.cc`.
2. Append these lines to the top of file (after the `#include`s)
    ```python
    #ifdef _MSC_VER
    #include <algorithm>
    #define fmin(a, b) std::min(a, b)
    #define fmax(a, b) std::max(a, b)
    #endif
  ```

3. In that file (`common/maskApi.cc`) search for all occurences of `malloc` and cast them to the appropriate type, i.e.:
change `malloc(sizeof(<type>)*<const>)` to `(<type>*)malloc(sizeof(<type>)*<const>)`.
4. In `PythonAPI/pycocotools/_mask.pyx` change these line (in the beginning of the file)
    ```
    # distutils: language = c
    # distutils: sources = ../common/maskApi.c
    ```
    to these
    ```
    # distutils: language = c++
    # distutils: sources = ../common/maskApi.cc
    ```

5. And finally a few changes in `PythonAPI/setup.py`
  1. Add `import sys`
  2. Add these lines after the comments:
    ```
    extra_compile_args = ['-Wno-cpp', '-Wno-unused-function', '-std=c99']\  
    if sys.platform != 'win32' else []  
    ```
  
  3. Finally change `Extension(...)` to this:
    ```
    Extension(
        'pycocotools._mask',
        language='c++',
        sources=['../common/maskApi.cc', 'pycocotools/_mask.pyx'],
        include_dirs = [np.get_include(), '../common'],
        extra_compile_args=extrac_compiler_args,
    )
    ```
    
That's it.

**Bonus**. If when compiling, you see the `can't find vcvarsall.bat` error [-(, then do this:
In the root folder, execute `pip install -e PythonAPI`, since `setuptools` probably does better job of finding where the hell `vcvarsall.bat` is.

**Disclailmer**: This is only tested on Python 2.7.12 and using the latest version ([2934299](https://github.com/pdollar/coco/commit/2934299ee051a601648ee4852b303e1c820aa02e)) from the [pdollar/coco](https://github.com/pdollar/coco).
