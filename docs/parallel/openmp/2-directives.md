---
title: 2. 指令
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424193"
---
# <a name="2-directives"></a>2.指令

指令基于 C 和C++标准中定义 `#pragma` 指令。  支持 OpenMP C 和C++ API 的编译器将包含一个命令行选项，该选项可激活并允许解释所有 OpenMP 编译器指令。

## <a name="21-directive-format"></a>2.1 指令格式

OpenMP 指令的语法由[附录 C](c-openmp-c-and-cpp-grammar.md)中的语法正式指定，非正式方式如下：

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每个指令都从 `#pragma omp`开始，以减少与其他（非 OpenMP 或供应商扩展到 OpenMP）的杂注指令发生冲突的可能性。 指令的其余部分遵循编译器指令 C 和C++标准的约定。 具体而言，可以在 `#`前后使用空白，有时必须使用空格分隔指令中的单词。 在 `#pragma omp` 后面的预处理令牌可能会被宏替换。

指令区分大小写。 子句出现在指令中的顺序并不重要。 根据需要，根据每个子句的说明中列出的限制，可以重复使用指令上的子句。 如果子句中出现*变量列表*，则它必须仅指定变量。 只能为每个指令指定一个*指令名称*。  例如，不允许使用以下指令：

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指令最多适用于一个后续语句，该语句必须是结构化块。

## <a name="22-conditional-compilation"></a>2.2 条件编译

`_OPENMP` 的宏名称由 OpenMP 兼容的实现定义为十进制常量*yyyymm*，这将是已批准规范的年份和月份。 此宏不得是 `#define` 或 `#undef` 预处理指令的主题。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果供应商定义 OpenMP 的扩展，则可以指定其他预定义的宏。

## <a name="23-parallel-construct"></a>2.3 并行构造

以下指令定义了一个并行区域，这是程序的一个区域，该区域由多个线程并行执行。 此指令是启动并行执行的基本构造。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是以下项之一：

- `if(`*标量表达式*`)`
- `private(`*变量-列表*`)`
- `firstprivate(`*变量-列表*`)`
- `default(shared | none)`
- `shared(`*变量-列表*`)`
- `copyin(`*变量-列表*`)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(`*整数表达式*`)`

当线程返回到并行构造时，如果下列情况之一为真，则会创建一个线程团队：

- 不存在 `if` 子句。
- `if` 表达式的计算结果为非零值。

此线程将成为团队的主线程，线程数为0，组中的所有线程（包括主线程）并行执行区域。 如果 `if` 表达式的值为零，则将对该区域进行序列化。

若要确定请求的线程数，请按顺序考虑以下规则。 将应用满足条件的第一个规则：

1. 如果 `num_threads` 子句存在，则整数表达式的值为请求的线程数。

1. 如果已调用 `omp_set_num_threads` 库函数，则最近执行的调用中的自变量的值是请求的线程数。

1. 如果定义了环境变量 `OMP_NUM_THREADS`，则此环境变量的值为请求的线程数。

1. 如果未使用上述方法中的任何一个，则请求的线程数是实现定义的。

如果 `num_threads` 子句存在，则它将取代 `omp_set_num_threads` 库函数或 `OMP_NUM_THREADS` 环境变量所请求的线程的数目。 以后的并行区域不受其影响。

执行并行区域的线程数还取决于是否启用了动态调整线程数。 如果禁用动态调整，则请求的线程数将执行并行区域。 如果启用了动态调整，则请求的线程数是可能执行并行区域的最大线程数。

如果在对线程数进行动态调整时遇到并行区域，并且并行区域请求的线程数大于运行时系统可以提供的数目，则程序的行为是实现定义的。 例如，实现可能会中断程序的执行，也可能会序列化并行区域。

`omp_set_dynamic` 库函数和 `OMP_DYNAMIC` 环境变量可用于启用和禁用动态调整线程数。

在任意给定时间，实际承载线程的物理处理器的数量是实现定义的。 创建后，团队中的线程数在该并行区域的持续时间内保持不变。 它可以由用户显式更改，也可以由运行时系统通过一个并行区域自动进行更改。

并行区域内包含的语句由每个线程执行，每个线程可以执行与其他线程不同的语句的路径。 并行区域的词法范围外遇到的指令称为孤立指令。

并行区域结束时有隐含的障碍。 只有团队的主线程在并行区域结束时继续执行。

如果执行并行区域的团队中的线程遇到其他并行构造，则会创建一个新团队，并成为该新团队的主节点。 默认情况下将序列化嵌套的并行区域。 因此，默认情况下，嵌套的并行区域由一个线程组成的团队执行。 通过使用运行时库函数 `omp_set_nested` 或环境变量 `OMP_NESTED`，可以更改默认行为。 但是，执行嵌套并行区域的团队中的线程数是实现定义的。

`parallel` 指令的限制如下所示：

- 指令上最多可以出现一个 `if` 子句。

- 未指定是否会出现 if 表达式或 `num_threads` 表达式中的任何副作用。

- 并行区域内执行的 `throw` 必须使执行在同一结构化块的动态范围内恢复，并且必须由引发异常的同一线程捕获。

- 指令上只能出现一个 `num_threads` 子句。 在并行区域的上下文之外计算 `num_threads` 表达式，其计算结果必须为正整数值。

- 未指定 `if` 和 `num_threads` 子句的计算顺序。

### <a name="cross-references"></a>交叉引用

- `private`、`firstprivate`、`default`、`shared`、`copyin`和 `reduction` 子句（[section 2.7.2](#272-data-sharing-attribute-clauses)）
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)库函数
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)环境变量
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)函数
- [OMP_NESTED](4-environment-variables.md#44-omp_nested)环境变量
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)库函数

## <a name="24-work-sharing-constructs"></a>2.4 工作共享构造

工作共享构造将关联语句的执行分布到遇到该语句的团队成员中。 工作共享指令不会启动新线程，并且进入工作共享构造时不会有隐含的障碍。

为团队中的每个线程所遇到的工作共享构造和 `barrier` 指令的顺序必须相同。

OpenMP 定义以下工作共享构造，并在以下各节中描述这些构造：

- [for](#241-for-construct)指令
- [sections](#242-sections-construct)指令
- [单个](#243-single-construct)指令

### <a name="241-for-construct"></a>构造的2.4。1

`for` 指令标识了一个迭代工作共享构造，该构造指定将并行执行关联循环的迭代。 `for` 循环的迭代分布于在执行它所绑定到的并行构造的团队中已经存在的线程中。 `for` 构造的语法如下所示：

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句是以下项之一：

- `private(`*变量-列表*`)`
- `firstprivate(`*变量-列表*`)`
- `lastprivate(`*变量-列表*`)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

`for` 指令对相应 `for` 循环的结构施加限制。 具体而言，相应的 `for` 循环必须具有规范形状：

`for (` *init-expr* `;` *var  logical-op  b* `;` *incr-expr* `)`

*init-expr*<br/>
以下项之一：

- *var* = *lb*
- *integer-type var* = *lb*

*incr-expr*<br/>
以下项之一：

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
带符号的整数变量。 如果此变量在其他情况下是共享的，则它在 `for`的持续时间内隐式变为专用。 请勿在 `for` 语句的主体内修改此变量。 除非 `lastprivate`指定变量，否则在循环后其值不确定。

*logical-op*<br/>
以下项之一：

- `<`
- `<=`
- `>`
- `>=`

*lb*、 *b*和*增量*<br>
循环固定整数表达式。 在计算这些表达式时没有同步，因此任何计算的副作用都会产生不确定的结果。

规范形式允许在进入循环时计算循环迭代的次数。 此计算是在整型提升后，用*var*类型的值进行的。 具体而言，如果*b*的值 `-` *lb* `+`*增量*不能用该类型表示，则结果是不确定的。 此外，如果*逻辑 op*为 `<` 或 `<=`，则*增量-expr*必须导致循环的每次迭代增加*var* 。   如果*逻辑 op*为 `>` 或 `>=`，则*增量-expr*必须在循环的每次迭代上导致*var*变得更小。

`schedule` 子句指定如何在组的线程之间划分 `for` 循环的迭代。 程序的正确性不得依赖于哪个线程执行特定迭代。 *Chunk_size*的值（如果指定）必须是具有正值的循环固定整数表达式。 在计算此表达式时没有同步，因此任何计算的副作用都会产生不确定的结果。 计划*类型*可以是以下值之一：

表2-1： `schedule` 子句*类型*值

|||
|-|-|
|static|当指定 `schedule(static,` *chunk_size* `)` 时，迭代将被划分为*chunk_size*指定的大小的块区。 块以循环方式按线程编号的顺序静态分配给团队中的线程。 如果未 *使用 chunk_size* 迭代空间划分为与分配给每个线程一个区块的大小，大致相等的块的指定。|
|dynamic|当指定 `schedule(dynamic,` *chunk_size* `)` 时，迭代分为一系列块区，其中每个块包含*chunk_size*迭代。 每个区块都分配到等待分配的线程。 线程执行迭代的区块，然后等待其下一次分配，直到没有剩余的区块被分配。 要分配的最后一个块区的迭代次数可能较小。 如果未指定*chunk_size* ，则默认为1。|
|按|当指定 `schedule(guided,` *chunk_size* `)` 时，迭代将分配给大小减小的区块中的线程。 线程完成其已分配的迭代块后，会动态分配另一个区块，直到没有剩余的块。 有关 *使用 chunk_size*的每个块区大小为 1，是大约未分配的线程数除以的迭代数。 这些大小几乎以指数方式减为1。 对于值*k*大于1的*chunk_size* ，大小几乎以指数方式减小到*k*，只不过最后一个块区的迭代数可能小于*k* 。 如果未指定*chunk_size* ，则默认为1。|
|Runtime — 运行时|当指定 `schedule(runtime)` 时，有关计划的决策将推迟到运行时。 可以在运行时通过将环境变量设置 `OMP_SCHEDULE`来选择区块的计划*类型*和大小。 如果未设置此环境变量，则生成的计划是实现定义的。 指定 `schedule(runtime)` 时，不得指定*chunk_size* 。|

如果没有显式定义的 `schedule` 子句，则默认 `schedule` 是实现定义的。

与 OpenMP 兼容的程序不应依赖特定的计划来执行正确的执行。 程序不应依赖于上面给出的说明完全一致的计划*类型*，因为在不同的编译器中，同一计划*类型*的实现可以有不同之处。 这些说明可用于选择适用于特定情况的计划。

当 `ordered` 指令绑定到 `for` 构造时，必须存在 `ordered` 子句。

除非指定了 `nowait` 子句，否则 `for` 构造的末尾存在隐式屏障。

`for` 指令的限制如下所示：

- `for` 循环必须是结构化块，另外，它的执行必须不能由 `break` 语句终止。

- 与 `for` 指令关联的 `for` 循环的循环控制表达式的值必须对团队中的所有线程都是相同的。

- `for` 循环迭代变量必须具有有符号的整数类型。

- `for` 指令上只能出现一个 `schedule` 子句。

- `for` 指令上只能出现一个 `ordered` 子句。

- `for` 指令上只能出现一个 `nowait` 子句。

- 如果出现*chunk_size*、 *lb*、 *b*或*增量*表达式中的任何副作用，则该方法为未指定的。

- 对于团队中的所有线程， *chunk_size*表达式的值必须相同。

#### <a name="cross-references"></a>交叉引用

- `private`、`firstprivate`、`lastprivate`和 `reduction` 子句（[section 2.7.2](#272-data-sharing-attribute-clauses)）
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)环境变量
- [顺序](#266-ordered-construct)构造
- [schedule](d-using-the-schedule-clause.md)子句

### <a name="242-sections-construct"></a>2.4.2 sections 节构造

`sections` 指令标识 noniterative 的工作共享构造，该构造指定一组要在团队中的线程之间划分的构造。 每个部分由团队中的一个线程执行一次。 `sections` 指令的语法如下所示：

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句是以下项之一：

- `private(`*变量-列表*`)`
- `firstprivate(`*变量-列表*`)`
- `lastprivate(`*变量-列表*`)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

每个部分前面都有一个 `section` 指令，不过 `section` 指令对于第一个部分是可选的。 `section` 指令必须出现在 `sections` 指令的词法范围内。 如果未指定 `nowait`，则 `sections` 构造的末尾有一个隐式屏障。

`sections` 指令的限制如下所示：

- `section` 指令不得出现在 `sections` 指令的词法范围之外。

- `sections` 指令上只能出现一个 `nowait` 子句。

#### <a name="cross-references"></a>交叉引用

- `private`、`firstprivate`、`lastprivate`和 `reduction` 子句（[section 2.7.2](#272-data-sharing-attribute-clauses)）

### <a name="243-single-construct"></a>2.4.3 单构造

`single` 指令标识一个构造，该构造指定关联的结构化块仅由团队中的一个线程执行（不一定是主线程）。 `single` 指令的语法如下所示：

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句是以下项之一：

- `private(`*变量-列表*`)`
- `firstprivate(`*变量-列表*`)`
- `copyprivate(`*变量-列表*`)`
- `nowait`

除非指定了 `nowait` 子句，否则 `single` 构造后会出现隐式屏障。

`single` 指令的限制如下所示：

- `single` 指令上只能出现一个 `nowait` 子句。
- `copyprivate` 子句不得与 `nowait` 子句一起使用。

#### <a name="cross-references"></a>交叉引用

- `private`、`firstprivate`和 `copyprivate` 子句（[section 2.7.2](#272-data-sharing-attribute-clauses)）

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 组合的并行工作共享构造

组合的并行工作共享构造是用于指定只有一个工作共享构造的并行区域的快捷方式。 这些指令的语义与显式指定 `parallel` 指令后接单个工作共享构造相同。

以下部分介绍了组合的并行工作共享构造：

- [对指令并行](#251-parallel-for-construct)
- [并行节](#252-parallel-sections-construct)指令

### <a name="251-parallel-for-construct"></a>2.5.1 并行构造

`parallel for` 指令是只包含单个 `for` 指令的 `parallel` 区域的快捷方式。 `parallel for` 指令的语法如下所示：

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

此指令允许 `parallel` 指令的所有子句和 `for` 指令（`nowait` 子句除外），其含义和限制相同。 语义与显式指定 `parallel` 指令后跟 `for` 指令相同。

#### <a name="cross-references"></a>交叉引用

- [并行](#23-parallel-construct)指令
- [for](#241-for-construct)指令
- [数据 attribute 子句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 并行节构造

`parallel sections` 指令提供了一个快捷方式窗体，用于指定只有一个 `sections` 指令的 `parallel` 区域。 语义与显式指定 `parallel` 指令后跟 `sections` 指令相同。 `parallel sections` 指令的语法如下所示：

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是 `parallel` 和 `sections` 指令接受的子句之一，`nowait` 子句除外。

#### <a name="cross-references"></a>交叉引用

- [并行](#23-parallel-construct)指令
- [sections](#242-sections-construct)指令

## <a name="26-master-and-synchronization-directives"></a>2.6 Master 和同步指令

以下部分介绍：

- [主](#261-master-construct)构造
- [关键](#262-critical-construct)构造
- [关卡](#263-barrier-directive)指令
- [原子](#264-atomic-construct)构造
- [flush](#265-flush-directive)指令
- [顺序](#266-ordered-construct)构造

### <a name="261-master-construct"></a>2.6.1 主构造

`master` 指令标识指定由团队的主线程执行的结构化块的构造。 `master` 指令的语法如下所示：

```cpp
#pragma omp master new-linestructured-block
```

团队中的其他线程不执行关联的结构化块。 进入或退出主构造时，没有隐含的障碍。

### <a name="262-critical-construct"></a>2.6.2 临界构造

`critical` 指令标识一种构造，该构造将关联的结构化块的执行限制为一次一个线程。 `critical` 指令的语法如下所示：

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

可选*名称*可用于标识关键区域。 用于标识关键区域的标识符具有外部链接，并且位于与标签、标记、成员和普通标识符所使用的命名空间不同的命名空间中。

线程在关键区域开始时等待，直到没有其他线程执行具有相同名称的关键区域（在程序中的任何位置）。 所有未命名 `critical` 指令映射到相同的未指定名称。

### <a name="263-barrier-directive"></a>2.6.3 关卡指令

`barrier` 指令同步组中的所有线程。 如果遇到这种情况，则团队中的每个线程都将等待，直到其他线程到达此点。 `barrier` 指令的语法如下所示：

```cpp
#pragma omp barrier new-line
```

在团队中的所有线程都遇到关卡后，团队中的每个线程都将开始并行执行关卡指令后的语句。 由于 `barrier` 指令没有 C 语言语句作为其语法的一部分，因此在程序中对其位置存在一些限制。 有关正式语法的详细信息，请参阅[附录 C](c-openmp-c-and-cpp-grammar.md)。下面的示例说明了这些限制。

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 原子构造

`atomic` 指令可确保以原子方式更新特定内存位置，而不是将其公开给多个同时写入的线程。 `atomic` 指令的语法如下所示：

```cpp
#pragma omp atomic new-lineexpression-stmt
```

Expression 语句必须具有以下形式之一：

- *x binop* `=` *expr*
- *x* `++`
- `++` x
- *x* `--`
- `--` x

在前面的表达式中：

- *x*是带有标量类型的左值表达式。

- *expr*是具有标量类型的表达式，它不引用*x*指定的对象。

- *binop*不是一个重载运算符，是 `+`、`*`、`-`、`/`、`&`、`^`、`|`、`<<`或 `>>`之一。

尽管它是实现定义的，但实现是否将所有 `atomic` 指令替换为具有相同的唯一*名称*的 `critical` 指令，`atomic` 指令可以更好地进行优化。 通常，可以使用最小开销执行原子更新的硬件说明。

只有*x*指定的对象的负载和存储是原子的;*expr*的计算不是原子的。 若要避免争用条件，应以并行 `atomic` 方式保护位置的所有更新，而不是已知没有争用情况的那些更新。

`atomic` 指令的限制如下所示：

- 对整个程序中存储位置 x 的所有原子引用都需要具有兼容的类型。

#### <a name="examples"></a>示例

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 flush 指令

`flush` 指令（无论是显式的还是隐式的）指定一个 "跨线程" 序列点，要求实现该序列点以确保团队中的所有线程都在内存中具有特定对象（在下面指定）的一致视图。 这意味着，引用这些对象的表达式的以前计算已完成，后续评估尚未开始。 例如，编译器必须将对象的值还原为内存，硬件可能需要将写入缓冲区刷新到内存中，并从内存中重载对象的值。

`flush` 指令的语法如下所示：

```cpp
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步的对象都可以由变量指定，则可以在可选的*变量列表*中指定这些变量。 如果指针在*变量列表*中存在，则将刷新指针本身，而不是指针引用的对象。

不带*变量列表*的 `flush` 指令将同步除自动存储持续时间以外的不可访问对象之外的所有共享对象。 （这可能比带有*变量列表*的 `flush` 开销更大。）不带*变量列表*的 `flush` 指令隐含为以下指令：

- `barrier`
- 进入和退出 `critical`
- 进入和退出 `ordered`
- 进入和退出 `parallel`
- 退出 `for`
- 退出 `sections`
- 退出 `single`
- 进入和退出 `parallel for`
- 进入和退出 `parallel sections`

如果存在 `nowait` 子句，则不暗示指令。 应注意的是，`flush` 指令对于以下任何情况都不隐含：

- 进入 `for`
- 进入或退出 `master`
- 进入 `sections`
- 进入 `single`

访问具有可变限定类型的对象的值的引用的行为就像在上一个序列点指定该对象的 `flush` 指令一样。 修改具有可变限定类型的对象的值的引用的行为就像在后续序列点指定该对象的 `flush` 指令一样。

由于 `flush` 指令没有 C 语言语句作为其语法的一部分，因此在程序中对其位置存在一些限制。 有关正式语法的详细信息，请参阅[附录 C](c-openmp-c-and-cpp-grammar.md)。下面的示例说明了这些限制。

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

`flush` 指令的限制如下所示：

- `flush` 指令中指定的变量不能具有引用类型。

### <a name="266-ordered-construct"></a>2.6.6 顺序构造

遵循 `ordered` 指令的结构化块按顺序循环中执行迭代的顺序执行。 `ordered` 指令的语法如下所示：

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered` 指令必须在 `for` 或 `parallel for` 构造的动态范围内。 `ordered` 构造绑定的 `for` 或 `parallel for` 指令必须具有指定的 `ordered` 子句，如[2.4.1 部分](#241-for-construct)中所述。 在使用 `ordered` 子句执行 `for` 或 `parallel for` 构造时，将严格按照顺序执行循环中执行的顺序来严格执行 `ordered` 构造。

`ordered` 指令的限制如下所示：

- 具有 `for` 构造的循环迭代不得多次执行相同的有序指令，并且它不能执行多个 `ordered` 指令。

## <a name="27-data-environment"></a>2.7 数据环境

本部分介绍了用于在并行区域执行期间控制数据环境的指令和多个子句，如下所示：

- 提供[threadprivate](#271-threadprivate-directive)指令是为了使文件范围、命名空间范围或静态块范围变量成为线程的局部变量。

- 在并行或工作共享构造期间，可以在指令上指定的子句来控制变量的共享属性，如[2.7.2 部分](#272-data-sharing-attribute-clauses)中所述。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指令

`threadprivate` 指令使命名的文件范围、命名空间范围或静态块范围变量在专用于线程的*变量列表*中指定。 *变量列表*是一个以逗号分隔的变量列表，其中不包含不完整的类型。 `threadprivate` 指令的语法如下所示：

```cpp
#pragma omp threadprivate(variable-list) new-line
```

`threadprivate` 变量的每个副本将在第一次引用该副本之前的程序中的一个未指定点初始化一次，并以常规方式（即，因为在程序的串行执行过程中将初始化主副本）。 请注意，如果在 `threadprivate` 变量的显式初始值设定项中引用某个对象，并且在第一次引用该变量之前修改了该对象的值，则该行为是未指定的。

与任何专用变量一样，线程不得引用 `threadprivate` 对象的另一个线程副本。 在程序的序列区域和主区域期间，引用将指向对象的主线程副本。

在第一个并行区域执行后，仅当动态线程机制已禁用并且所有并行区域的线程数保持不变时，才能保证 `threadprivate` 对象中的数据保持不变。

对 `threadprivate` 指令的限制如下所示：

- 文件范围或命名空间范围变量的 `threadprivate` 指令必须出现在任何定义或声明的外部，并且必须在词法上指向其列表中的任何变量的所有引用。

- 文件或命名空间范围内的 `threadprivate` 指令的*变量列表*中的每个变量都必须引用在词法上位于该指令前面的文件或命名空间范围内的变量声明。

- 静态块范围变量的 `threadprivate` 指令必须出现在变量的作用域中，而不是嵌套作用域中。 指令必须在词法上置于对其列表中任何变量的所有引用之前。

- 块范围内 `threadprivate` 指令的*变量列表*中的每个变量都必须引用在词法上位于该指令前面的同一范围内的变量声明。 变量声明必须使用静态存储类说明符。

- 如果在一个翻译单元中的 `threadprivate` 指令中指定了变量，则必须在声明它的每个翻译单元中的 `threadprivate` 指令中指定该变量。

- `threadprivate` 变量不能出现在除 `copyin`、`copyprivate`、`schedule`、`num_threads`或 `if` 子句之外的任何子句中。

- `threadprivate` 变量的地址不是地址常数。

- `threadprivate` 变量不能具有不完整的类型或引用类型。

- 如果使用显式初始值设定项进行声明，则具有非 POD 类类型的 `threadprivate` 变量必须具有可访问的、明确的复制构造函数。

下面的示例演示如何修改在初始值设定项中显示的变量可能导致未指定的行为，还说明如何通过使用辅助对象和复制构造函数来避免此问题。

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>交叉引用

- [动态线程](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)环境变量

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 数据共享特性子句

若干指令接受允许用户在区域期间控制变量共享属性的子句。 共享特性子句仅适用于出现子句的指令的词法范围中的变量。 并非所有指令都允许使用以下子句。 对特定指令有效的子句的列表与指令一起介绍。

如果当遇到并行或工作共享构造时，变量是可见的，并且在共享 attribute 子句或 `threadprivate` 指令中未指定变量，则会共享该变量。 共享并行区域动态范围内声明的静态变量。 共享堆分配的内存（例如，使用 C C++中的 `malloc()` 或中C++的 `new` 运算符）。 （但是，指向此内存的指针可以是私有的或共享的。）在并行区域的动态范围内声明的具有自动存储持续时间的变量是专用的。

大多数子句都接受*变量列表*参数，该参数是可见变量的逗号分隔列表。 如果数据共享特性子句中引用的变量具有从模板派生的类型，并且在程序中没有对该变量的其他引用，则该行为是不确定的。

指令子句中显示的所有变量都必须可见。 子句可以根据需要重复执行，但不能在多个子句中指定变量，只不过可以同时在 `firstprivate` 和 `lastprivate` 子句中指定变量。

以下各节介绍数据共享特性子句：

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private` 子句将变量列表中的变量声明为组中的每个线程专用。 `private` 子句的语法如下所示：

```cpp
private(variable-list)
```

`private` 子句中指定的变量的行为如下所示。 将为构造分配一个具有自动存储持续时间的新对象。 新对象的大小和对齐方式取决于变量的类型。 此分配对团队中的每个线程发生一次，并在必要时为类对象调用默认构造函数。否则，初始值是不确定的。  变量引用的原始对象在进入构造时具有不确定的值，不能在构造的动态范围内修改，并且在从构造中退出时具有不确定的值。

在指令构造的词法范围内，变量引用由线程分配的新的私有对象。

`private` 子句的限制如下所示：

- 在 `private` 子句中指定的类类型的变量必须具有可访问的、明确的默认构造函数。

- `private` 子句中指定的变量不能具有 `const`限定的类型，除非它具有具有 `mutable` 成员的类类型。

- `private` 子句中指定的变量不能具有不完整的类型或引用类型。

- 在绑定到并行构造的工作共享指令上，不能在 `private` 子句中指定在 `parallel` 指令的 `reduction` 子句中显示的变量。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate` 子句提供 `private` 子句提供的功能的超集。 `firstprivate` 子句的语法如下所示：

```cpp
firstprivate(variable-list)
```

*变量列表*中指定的变量具有 `private` 子句语义，如[2.7.2.1 部分](#2721-private)中所述。 初始化或构造的发生方式就像在线程的构造执行之前，在每个线程上执行一次。 对于并行构造中的 `firstprivate` 子句，新的私有对象的初始值是最初在遇到它的线程的并行构造之前存在的原始对象的值。 对于工作共享构造中的 `firstprivate` 子句，执行工作共享构造的每个线程的新专用对象的初始值是在同一线程遇到工作共享构造的时间点之前存在的原始对象的值。 此外，对于C++对象，每个线程的新专用对象都是从原始对象构造的副本。

`firstprivate` 子句的限制如下所示：

- `firstprivate` 子句中指定的变量不能具有不完整的类型或引用类型。

- 指定为 `firstprivate` 的类类型的变量必须具有可访问的、明确的复制构造函数。

- 不能在绑定到并行构造的工作共享指令的 `firstprivate` 子句中指定并行区域内或出现在 `parallel` 指令的 `reduction` 子句中的私有变量。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate` 子句提供 `private` 子句提供的功能的超集。 `lastprivate` 子句的语法如下所示：

```cpp
lastprivate(variable-list)
```

*变量列表*中指定的变量具有 `private` 子句语义。 如果 `lastprivate` 子句出现在标识工作共享构造的指令上，则会将每个 `lastprivate` 变量的值从关联循环的顺序上一次迭代中，或词法上的最后一个节指令分配给该变量的原始对象。 不是由 `for` 或 `parallel for`的最后一个迭代或 `sections` 或 `parallel sections` 指令的词法上最后一个部分赋予值的变量在构造后具有不确定的值。 未分配的子数组在构造后也有一个不确定的值。

`lastprivate` 子句的限制如下所示：

- 适用于 `private` 的所有限制。

- 指定为 `lastprivate` 的类类型的变量必须具有可访问的、明确的复制赋值运算符。

- 不能在绑定到并行构造的工作共享指令的 `lastprivate` 子句中指定并行区域内或出现在 `parallel` 指令的 `reduction` 子句中的私有变量。

#### <a name="2724-shared"></a>2.7.2.4 shared

此子句共享团队中所有线程的*变量列表*中显示的变量。 团队中的所有线程都将访问相同的 `shared` 变量存储区域。

`shared` 子句的语法如下所示：

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default` 子句允许用户影响变量的数据共享属性。 `default` 子句的语法如下所示：

```cpp
default(shared | none)
```

指定 `default(shared)` 等效于在 `shared` 子句中显式列出每个当前可见的变量，除非该变量 `threadprivate` 或 `const`限定的。 如果没有显式 `default` 子句，则默认行为与指定 `default(shared)` 时的行为相同。

指定 `default(none)` 要求对于对并行构造的词法范围内的变量的每个引用，必须至少满足以下条件之一：

- 在包含引用的构造的数据共享特性子句中显式列出了该变量。

- 此变量在并行构造中声明。

- 变量是 `threadprivate`的。

- 变量具有 `const`限定的类型。

- 变量是紧跟在 `for` 或 `parallel for` 指令后面的 `for` 循环的循环控制变量，变量引用出现在循环内。

在包含指令的 `firstprivate`、`lastprivate`或 `reduction` 子句上指定变量会导致隐式引用封闭上下文中的变量。 此类隐式引用也服从以上所列的要求。

`parallel` 指令上只能指定一个 `default` 子句。

可以使用 `private`、`firstprivate`、`lastprivate`、`reduction`和 `shared` 子句来重写变量的默认数据共享特性，如下面的示例所示：

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

此子句可对使用运算符*op*的*变量列表*中显示的标量变量进行缩减。 `reduction` 子句的语法如下所示：

`reduction(` *op* `:` *variable-list* `)`

通常为具有以下形式之一的语句指定缩减：

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* （减法除外）
- *x* `++`
- `++` x
- *x* `--`
- `--` x

其中：

*x*<br/>
列表中指定的一个缩减变量。

*variable-list*<br/>
以逗号分隔的标量缩减变量的列表。

*expr*<br/>
标量类型不引用*x*的表达式。

*op*<br/>
不是重载的运算符，但 `+`、`*`、`-`、`&`、`^`、`|`、`&&`或 `||`之一。

*binop*<br/>
不是 `+`、`*`、`-`、`&`、`^`或 `|`之一的重载运算符。

下面是 `reduction` 子句的示例：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

如示例中所示，运算符可能会隐藏在函数调用中。 用户应注意 `reduction` 子句中指定的运算符与缩减运算匹配。

尽管 `||` 运算符的右操作数在此示例中没有副作用，但仍允许使用它们，但应谨慎使用。 在这种情况下，在循环执行期间不会发生的副作用会在并行执行过程中发生。 出现这种差异的原因是迭代的执行顺序是不确定的。

运算符用于确定编译器用于减少的所有私有变量的初始值，并确定终结运算符。 显式指定运算符可以使减语句在构造的词法范围之外。 可以在指令中指定任意数量的 `reduction` 子句，但对于该指令，变量最多只能出现在一个 `reduction` 子句中。

将为每个线程创建一个变量*列表*中每个变量的私有副本，就如同使用 `private` 子句一样。 根据运算符初始化专用副本（请参阅下表）。

在为其指定 `reduction` 子句的区域末尾，将更新原始对象，以反映使用指定的运算符将其原始值与每个专用副本的最终值结合起来的结果。 缩减运算符都是关联（减法除外），编译器可以自由地重新关联最终值的计算。 （添加了减减的部分结果以构成最终值。）

当第一个线程到达包含子句时，原始对象的值将变为不确定，并一直保持到缩减计算完成。  通常，计算将在构造的末尾完成;但是，如果在还应用了 `nowait` 的构造上使用 `reduction` 子句，则原始对象的值将保持不变，直到执行了关卡同步，以确保所有线程都完成了 `reduction` 子句。

下表列出了有效的运算符及其规范的初始化值。 实际初始化值将与缩减变量的数据类型一致。

|Operator|初始化|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

`reduction` 子句的限制如下所示：

- `reduction` 子句中的变量类型必须对缩减运算符有效，但绝不允许使用指针类型和引用类型。

- `reduction` 子句中指定的变量不能是 `const`限定的。

- 不能在绑定到并行构造的工作共享指令的 `reduction` 子句中指定并行区域内或出现在 `parallel` 指令的 `reduction` 子句中的私有变量。

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

`copyin` 子句提供了一种机制，用于为执行并行区域的团队中的每个线程 `threadprivate` 变量分配相同的值。 对于 `copyin` 子句中指定的每个变量，会将团队主线程中的变量的值复制到并行区域开头的线程专用副本（如赋值）。 `copyin` 子句的语法如下所示：

```cpp

copyin(
variable-list
)
```

`copyin` 子句的限制如下所示：

- `copyin` 子句中指定的变量必须具有可访问的、明确的复制赋值运算符。

- `copyin` 子句中指定的变量必须是 `threadprivate` 变量。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate` 子句提供一种机制，用于使用私有变量将值从一个团队的一个成员广播到其他成员。 当提供此类共享变量很难（例如，在每个级别需要不同变量的递归中）时，可以使用共享变量作为值。 `copyprivate` 子句只能出现在 `single` 指令上。

`copyprivate` 子句的语法如下所示：

```cpp

copyprivate(
variable-list
)
```

`copyprivate` 子句对其变量列表中变量的影响在执行与 `single` 构造关联的结构化块之后，并且在团队中的任何线程之前在构造的结尾处离开关卡。 然后，在团队中的所有其他线程中，对于*变量列表*中的每个变量，该变量将在执行构造的结构化块的线程中使用相应变量的值进行定义（就像赋值）。

`copyprivate` 子句的限制如下所示：

- `copyprivate` 子句中指定的变量不能出现在同一 `single` 指令的 `private` 或 `firstprivate` 子句中。

- 如果在并行区域的动态范围内遇到带有 `copyprivate` 子句的 `single` 指令，则在 `copyprivate` 子句中指定的所有变量都必须在封闭上下文中是私有的。

- `copyprivate` 子句中指定的变量必须具有可访问的明确复制赋值运算符。

## <a name="28-directive-binding"></a>2.8 指令绑定

动态绑定指令必须遵循以下规则：

- `for`、`sections`、`single`、`master`和 `barrier` 指令将绑定到动态封闭的 `parallel`（如果存在），而不考虑该指令上可能存在的任何 `if` 子句的值。 如果当前未执行任何并行区域，则指令由仅由主线程组成的团队执行。

- `ordered` 指令绑定到动态封闭 `for`。

- `atomic` 指令对所有线程中的 `atomic` 指令强制执行独占访问，而不仅仅是针对当前团队。

- `critical` 指令对所有线程中的 `critical` 指令强制执行独占访问，而不仅仅是针对当前团队。

- 指令永远不能绑定到最近动态封闭 `parallel`之外的任何指令。

## <a name="29-directive-nesting"></a>2.9 指令嵌套

指令的动态嵌套必须遵循以下规则：

- 在另一个 `parallel` 中动态动态地建立一个 `parallel` 指令，除非启用嵌套并行，否则仅由当前线程组成的新团队。

- 绑定到相同 `parallel` 的 `for`、`sections`和 `single` 指令不允许相互嵌套。

- 不允许使用具有相同名称的 `critical` 指令彼此嵌套。 请注意，此限制不足以防止死锁。

- 如果指令绑定到与区域相同的 `ordered`，则在 `critical`、`master` 和 `parallel` 区域的动态范围内不允许 `for`、`sections`和 `single` 指令。

- 如果指令绑定到与区域相同的 `single`，则不允许在 `for`、`ordered`、`sections`、`master`、`critical` 和 `parallel` 区域的动态范围内使用 `barrier` 指令。

- 如果 `master` 指令与工作共享指令绑定到同一个 `parallel`，则不允许在 `for`、`sections`和 `single` 指令的动态范围内使用 `master` 指令。

- 如果指令绑定到与区域相同的 `parallel`，则不允许在 `critical` 区域的动态范围内使用 `ordered` 指令。

- 当并行区域外执行时，在并行区域内动态执行时允许的任何指令也是允许的。 在用户指定的并行区域外动态执行时，该指令由仅由主线程组成的团队执行。
