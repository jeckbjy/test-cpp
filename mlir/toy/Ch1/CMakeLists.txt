# For a better template to copy, see examples/standalone
cmake_minimum_required(VERSION 3.26)

project(toyc-ch1)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(LLVM REQUIRED CONFIG)
include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})
# set(LLVM_LINK_COMPONENTS Support)

llvm_map_components_to_libnames(llvm_libs support core irreader orcjit native target)

# add_toy_chapter(toyc-ch1
#   toyc.cpp
#   parser/AST.cpp
#   )

add_executable(toyc-ch1 toyc.cpp parser/AST.cpp)

include_directories(include/)
target_link_libraries(toyc-ch1 ${llvm_libs})
