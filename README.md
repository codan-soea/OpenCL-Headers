# OpenCL<sup>TM</sup> API Headers

This repository contains C language headers for the OpenCL API.

The authoritative public repository for these headers is located at:

https://github.com/KhronosGroup/OpenCL-Headers

Issues, proposed fixes for issues, and other suggested changes should be
created using Github.

## CMake Package
While the headers may just be copied as-is, this repository also contains a
CMake script with an install rule to allow for packaging the headers.

```bash
cmake -S . -B build -DCMAKE_INSTALL_PREFIX=/path/to/desired/prefix
cmake --build build --target install
```
 
To consume the package:

```bash
cmake path/to/opencl/app -DOpenCLHeaders_ROOT=/chosen/install/prefix
```

```cmake
cmake_minimum_required(VERSION 3.0)
cmake_policy(VERSION 3.0...)
add_executable(app main.cpp)
find_package(OpenCLHeaders REQUIRED)
target_link_libraries(app PRIVATE OpenCL::Headers)
```

## Branch Structure

The OpenCL API headers in this repository are Unified headers and are designed
to work with all released OpenCL versions.  This differs from previous OpenCL
API headers, where version-specific API headers either existed in separate
branches, or in separate folders in a branch.

## Compiling for a Specific OpenCL Version

By default, the OpenCL API headers in this repository are for the latest
OpenCL version (currently OpenCL 2.2).  To use these API headers to target
a different OpenCL version, an application may `#define` the preprocessor
value `CL_TARGET_OPENCL_VERSION` before including the OpenCL API headers.
The `CL_TARGET_OPENCL_VERSION` is a three digit decimal value representing
the OpenCL API version.

For example, to enforce usage of no more than the OpenCL 1.2 APIs, you may
include the OpenCL API headers as follows:

```c
#define CL_TARGET_OPENCL_VERSION 120
#include <CL/opencl.h>
```

## Directory Structure

```
README.md               This file
LICENSE                 Source license for the OpenCL API headers
CL/                     Unified OpenCL API headers tree
```

## License

See [LICENSE](LICENSE).

---

OpenCL and the OpenCL logo are trademarks of Apple Inc. used by permission by Khronos.
