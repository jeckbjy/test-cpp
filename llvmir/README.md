
# LLVM IR原理与实践

- [llvm IR原理与实践](https://zhuanlan.zhihu.com/p/625792239)
- [详解LLVM代码生成技术及在数据库中的应用](https://ost.51cto.com/posts/12905)
- [PgSQL · 特性分析· JIT 在数据仓库中的应用价值](http://mysql.taobao.org/monthly/2016/11/10/)
- [JIT in ClickHouse](https://clickhouse.com/blog/clickhouse-just-in-time-compiler-jit)

## 其他

``` 一些命令
clang -Xclang -ast-dump -fsyntax-only main.c
clang -S -emit-llvm main.c
clang -S -emit-llvm -O3 main.c
clang -cc1 -disable-O0-optnone -S -emit-llvm main.c
opt main.ll -S --O3
llc main.ll
clang main.ll -o main

可读形式&比特码形式转换
llvm-as main.ll
llvm-dis main.bc

整个流程:
.c --frontend--> AST --frontend--> LLVM IR --LLVM opt--> LLVM IR --LLVM llc--> .s Assembly --OS Assembler--> .o --OS Linker--> executable
```
