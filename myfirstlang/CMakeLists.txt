
cmake_minimum_required(VERSION 3.12)
project(myfirstlang VERSION 1.0.0 LANGUAGES C CXX DESCRIPTION "llvm my first language demo")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# include_directories("/opt/homebrew/opt/llvm/include/")
find_package(LLVM REQUIRED CONFIG)
include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

llvm_map_components_to_libnames(llvm_libs support core irreader orcjit native target)

add_executable(parser 02_parser.cpp)
target_link_libraries(parser ${LLVM_LIBRARIES})

add_executable(codegen 03_codegen.cpp)
target_link_libraries(codegen ${llvm_libs})

add_executable(jit 04_jit.cpp)
target_link_libraries(jit ${llvm_libs})

# clang++ -g 05_control_flow.cpp `llvm-config --cxxflags --ldflags --system-libs --libs core orcjit native` -O3 -o toy
add_executable(flow 05_control_flow.cpp)
target_link_libraries(flow ${llvm_libs})

add_executable(operator 06_operator.cpp)
target_link_libraries(operator ${llvm_libs})

add_executable(mut_var 07_mut_var.cpp)
target_link_libraries(mut_var ${llvm_libs})

# clang++ -g -O3 ../08_native.cpp `llvm-config --cxxflags --ldflags --system-libs --libs all` -o native
# add_executable(native 08_native.cpp)
# target_link_libraries(native ${llvm_libs})

add_executable(debug 09_debug.cpp)
target_link_libraries(debug ${llvm_libs})
