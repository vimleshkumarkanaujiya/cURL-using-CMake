# cURL using CMake
A sample CMakeLists.txt file for building source with the cURL library
## Refer these steps to build the source <a href="https://github.com/vimleshkumarkanaujiya/CMake">CMake</a>

Code :

``` cmake

cmake_minimum_required(VERSION 3.0)
project(XYZ)

# Find libcurl
find_package(CURL REQUIRED)
include_directories(${CURL_INCLUDE_DIR})

# Add your source files
add_executable(${PROJECT_NAME} your_source_files.cpp)

# Link against libcurl
target_link_libraries(${PROJECT_NAME} ${CURL_LIBRARIES})

```
