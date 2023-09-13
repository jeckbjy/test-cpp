# Ch2

```sh
# "/opt/homebrew/opt/llvm/include/"
# build 目录
mlir-tblgen -gen-dialect-decls Ops.td -o Ops.h.inc -I ~/mystudy/llvm/llvm-project/mlir/include
mlir-tblgen -gen-op-defs Ops.td -o Ops.cpp.inc -I ~/mystudy/llvm/llvm-project/mlir/include
mlir-tblgen -gen-dialect-decls Ops.td -o Dialect.h.inc -I ~/mystudy/llvm/llvm-project/mlir/include
mlir-tblgen -gen-dialect-defs Ops.td -o Dialect.cpp.inc -I ~/mystudy/llvm/llvm-project/mlir/include

```