## Laboratory work III
Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере CMake
## Tutorial

```shell
  ~/VS/TIMP/TheKamenski/workspace$ source ./scripts/activate 
  ~/VS/TIMP/TheKamenski/workspace$ git clone git@github.com:${GITHUB_USERNAME}/lab02.git projects/lab03
```shell
Cloning into 'projects/lab03'...
remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (18/18), done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 18 (delta 2), reused 15 (delta 1), pack-reused 0
Receiving objects: 100% (18/18), done.
Resolving deltas: 100% (2/2), done.
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace$ cd projects/lab03
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ git remote remove origin && git remote add origin git@github.com:${GITHUB_USERNAME}/lab03.git
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ g++ -std=c++11 -I./include -c sources/print.cpp
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ls print.o
print.o
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ nm print.o | grep print
```
```shell
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ar rvs print.a print.o
```
```shell
ar: creating print.a
a - print.o
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ file print.a
print.a: current ar archive
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example1.cpp
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ls example1.o
```
example1.o
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ g++ example1.o print.a -o example1
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ./example1 && echo
```
```shell
hello
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example2.cpp
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ nm example2.o
```
```shell
0000000000000000 V DW.ref.__gxx_personality_v0
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED2Ev
0000000000000000 n _ZNSt15__new_allocatorIcED5Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZSt21ios_base_library_initv
0000000000000000 r _ZStL19piecewise_construct
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ g++ example2.o print.a -o example2
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ./example2
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cat log.txt && echo
```
```shell
hello
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf example1.o example2.o print.o
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf print.a
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf example1 example2
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf log.txt
```
```shell
cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(print)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
```
```shell
cmake -H. -B_build
```
```shell
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.2.0
-- The CXX compiler identification is GNU 13.2.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.7s)
-- Generating done (0.0s)
-- Build files have been written to: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_build
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build
```
```shell
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build
```
```shell
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_build
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build --target print
```
```shell
[100%] Built target print
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build --target example1
```
```shell
[ 50%] Built target print
[100%] Built target example1
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build --target example2
```
```shell
[ 50%] Built target print
[100%] Built target example2
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ ls -la _build/libprint.a
```
```shell
-rw-rw-r-- 1 TheKamenski TheKamenski 2238 Apr 23 20:24 _build/libprint.a
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ _build/example1 && echo
```
```shell
hello
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ _build/example2 && cat log.txt && echo
```
```shell
hello
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf log.txt
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ git clone https://github.com/tp-labs/lab03 tmp
```
```shell
Cloning into 'tmp'...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61
Receiving objects: 100% (91/91), 1.02 MiB | 3.61 MiB/s, done.
Resolving deltas: 100% (41/41), done.
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ mv -f tmp/CMakeLists.txt .
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ rm -rf tmp
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cat CMakeLists.txt
```
```shell
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
```
```shell
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_build
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ cmake --build _build --target install
```
```shell
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_install/include
-- Installing: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/TheKamenski/VS/TIMP/TheKamenski/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ tree _install
```
```shell
_install
├── cmake
│   ├── print-config.cmake
│   └── print-config-noconfig.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

4 directories, 4 files
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ git add CMakeLists.txt
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ git commit -m "Added CMakeLists.txt"
```
```shell
[main b435a48] Added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt
```
```shell
  ~:~/VS/TIMP/TheKamenski/workspace/projects/lab03$ git push origin main
```
```shell
Enumerating objects: 21, done.
Counting objects: 100% (21/21), done.
Delta compression using up to 8 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (21/21), 4.48 KiB | 4.48 MiB/s, done.
Total 21 (delta 3), reused 17 (delta 2), pack-reused 0
remote: Resolving deltas: 100% (3/3), done.
To github.com:TheKamenski/lab03.git
 * [new branch]      main -> main
```

