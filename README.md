Clone of COCO API - http://cocodataset.org/
===========================================

# Original README:

COCO is a large image dataset designed for object detection, segmentation, person keypoints detection, stuff segmentation, and caption generation. This package provides Matlab, Python, and Lua APIs that assists in loading, parsing, and visualizing the annotations in COCO. Please visit http://cocodataset.org/ for more information on COCO, including for the data, paper, and tutorials. The exact format of the annotations is also described on the COCO website. The Matlab and Python APIs are complete, the Lua API provides only basic functionality.

In addition to this API, please download both the COCO images and annotations in order to run the demos and use the API. Both are available on the project website.

Please download, unzip, and place the images in: coco/images/

Please download and place the annotations in: coco/annotations/

For substantially more details on the API please see http://cocodataset.org/#download.

# This clone's README:

My (Andrei) contribution:
- To support numpy 1.18 and newer I had to do some [int casting](https://github.com/pasandrei/cocoapi/commit/32b08be3bfd928d2f48de0fc3e6b526cfd2d31fa)

To support Windows build and python3 we had to make [minor changes](https://github.com/cocodataset/cocoapi/compare/master...philferriere:master#diff-49ecc5c8e93163121e2cc2eb6b1fca2c) to:

- `PythonAPI/setup.py`
- `PythonAPI/pycocotools/coco.py`

To install this package, use `pip` as follows:

```
C:\Users\Andrei Popovici> pip install git+https://github.com/pasandrei/cocoapi.git#subdirectory=PythonAPI
Collecting git+https://github.com/pasandrei/cocoapi.git#subdirectory=PythonAPI
  Cloning https://github.com/pasandrei/cocoapi.git to c:\users\andrei~1\appdata\local\temp\pip-req-build-sbym3nfs
  Running command git clone -q https://github.com/pasandrei/cocoapi.git 'C:\Users\ANDREI~1\AppData\Local\Temp\pip-req-build-sbym3nfs'
Building wheels for collected packages: pycocotools
  Building wheel for pycocotools (setup.py) ... done
  Created wheel for pycocotools: filename=pycocotools-2.0.1-cp36-cp36m-win_amd64.whl size=87008 sha256=0ddc608e51ef01fb4e75f71d136580c977f337a67911a9caa880e6ebe82d4d27
  Stored in directory: C:\Users\ANDREI~1\AppData\Local\Temp\pip-ephem-wheel-cache-ybbjpu8n\wheels\5f\82\42\7d698a40e4eedc73691038f5de180b0fb0dc33b0fe9443c58e
Successfully built pycocotools
Installing collected packages: pycocotools
Successfully installed pycocotools-2.0.1
```

On Windows, you must have the Visual C++ 2015 build tools on your path. If you don't, make sure to install them from [here](https://go.microsoft.com/fwlink/?LinkId=691126):

![](img/download.png)

Then, run `visualcppbuildtools_full.exe` and select default options:

![](img/install.png)

# Why have the demo notebooks been moved into their own directory?

If you clone/fork the **original** repo, you may hit the following error when running the demo notebooks:

![](img/notebooks.png)

It happens because there is a `pycocotools` directory in the same folder as the notebooks. The python code being imported then is the **local** implementation of `pycocotools`, not the one installed with `pip`. To fix this issue, the demo notebooks have been moved to their own directory.

# why am I getting a `ModuleNotFoundError: No module named 'pycocotools._mask'` error in my code?

If you get this error, it is because the COCO library you are calling is **NOT** our version of the library. Instead, you are (inadvertently) referencing **a local copy** of the library. So, if you get this error, search the tree of import in your code for a reference to a local `pycocotools` library. Then, move or delete the local version.

