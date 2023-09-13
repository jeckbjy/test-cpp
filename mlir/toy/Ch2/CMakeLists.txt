# For a better template to copy, see examples/standalone
cmake_minimum_required(VERSION 3.26)

project(toyc-ch2)

# add_subdirectory(./include)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(LLVM_ROOT_DIR /Users/bj00153ml/mystudy/llvm/llvm-project)

find_package(LLVM REQUIRED CONFIG)
include_directories(${LLVM_INCLUDE_DIRS})
# include_directories($LLVM_ROOT_DIR/mlir/include $LLVM_ROOT_DIR/llvm/include)
add_definitions(${LLVM_DEFINITIONS})

llvm_map_components_to_libnames(llvm_libs support core irreader orcjit native target)

add_executable(toyc-ch2 toyc.cpp parser/AST.cpp mlir/MLIRGen.cpp mlir/Dialect.cpp)
# add_dependencies(toyc-ch2 ToyCh2OpsIncGen)

include_directories(include/)
target_link_libraries(toyc-ch2 ${llvm_libs})


# set(LLVM_LINK_COMPONENTS
#   Support
#   )

# add_toy_chapter(toyc-ch2
#   toyc.cpp
#   parser/AST.cpp
#   mlir/MLIRGen.cpp
#   mlir/Dialect.cpp

#   DEPENDS
#   ToyCh2OpsIncGen

#   )
# include_directories(include/)
# include_directories(${CMAKE_CURRENT_BINARY_DIR}/include/)
# target_link_libraries(toyc-ch2
#   PRIVATE
#     MLIRAnalysis
#     MLIRFunctionInterfaces
#     MLIRIR
#     MLIRParser
#     MLIRSideEffectInterfaces
#     MLIRTransforms)
