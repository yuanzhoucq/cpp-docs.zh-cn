---
title: 2. 指令
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087335"
---
# <a name="2-directives"></a>2.指令

基于指令`#pragma`C 和 c + + 标准中定义的指令。  OpenMP C 和 c + + API 支持的编译器将包括激活并允许所有 OpenMP 编译器指令的解释的命令行选项。

## <a name="21-directive-format"></a>2.1 指令格式

该语法进行了正式指定 OpenMP 指令的语法[附录 C](c-openmp-c-and-cpp-grammar.md)，和非正式的方式，如下所示：

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每个指令开头`#pragma omp`，以减少与具有相同名称的其他 （非 OpenMP 或供应商扩展与 OpenMP） 杂注指令发生冲突的可能性。 指令的其余部分遵循编译器指令的 C 和 c + + 标准的约定。 之前和之后具体而言，可以使用空白`#`，并有时必须使用空格分隔指令中的单词。 预处理标记遵循`#pragma omp`宏替换。

指令是区分大小写。 子句在指令中的显示的顺序并不重要。 根据需要每个子句的说明中列出的限制的制约，可能会重复指令上的子句。 如果*变量列表*将出现在子句中，它必须指定只有变量。 只有一个*指令名称*可以指定每个指令。  例如，不允许使用以下指令：

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指令适用于最多一个后续语句，该语句必须是结构化的块中。

## <a name="22-conditional-compilation"></a>2.2 条件编译

`_OPENMP`宏名称指由符合 OpenMP 的实现的十进制常数*yyyymm*，它将是年份和月份的已批准的规范。 此宏的使用者不能`#define`或`#undef`预处理指令。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果供应商定义扩展，OpenMP，他们可以指定其他预定义的宏。

## <a name="23-parallel-construct"></a>2.3 parallel 构造

以下指令定义并行区域，这是由多个线程并行执行的程序的区域。 此指令是开始并行执行的基本构造。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*子句*是以下之一：

- `if(` *scalar-expression* `)`
- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `default(shared | none)`
- `shared(` *variable-list* `)`
- `copyin(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(` *integer-expression* `)`

当某个线程获取到并行构造时，以下情况之一，则会创建线程团队：

- 不`if`子句。
- `if`表达式的计算结果为非零值。

此线程将成为团队使用的线程编号是 0，主线程和团队，其中包括，在主线程中的所有线程并行都执行区域。 如果的值`if`表达式为零，则序列化该区域。

若要确定请求的线程数，将按顺序考虑以下规则。 将应用第一个满足其条件的规则：

1. 如果`num_threads`子句为存在，则整数表达式的值是所请求的线程数。

1. 如果`omp_set_num_threads`尚未调用库函数，则最近执行的调用中参数的值是所请求的线程数。

1. 如果环境变量`OMP_NUM_THREADS`定义，则此环境变量的值是所请求的线程数。

1. 如果没有上述两种方法使用，请求的线程数是实现定义。

如果`num_threads`子句存在，则它将取代请求的线程数`omp_set_num_threads`库函数或`OMP_NUM_THREADS`并行区域应用到环境变量。 更高版本的并行区域不受其影响。

执行并行区域的线程数还取决于是否启用了动态调整线程数。 如果禁用了动态调整，则请求的线程数会执行并行区域。 如果启用了动态调整请求的线程数是最大的可能执行并行区域的线程数。

如果禁用动态调整线程数，并为并行区域请求的线程数不只是运行时系统可以提供的号时遇到并行区域，则该程序的行为是实现定义。 实现可能会例如，中断执行程序，或者它可能将并行区域的序列化。

`omp_set_dynamic`库函数和`OMP_DYNAMIC`环境变量可用于启用和禁用动态调整线程数。

在任何给定时间实际托管线程的物理处理器的数目是实现定义的。 创建后，团队中的线程数保持不变的并行区域内。 可以由用户显式或通过从一个并行区域到另一个运行时系统会自动对其进行更改。

并行区域的动态范围内包含的语句执行的每个线程，并且每个线程可以执行不同于其他线程的语句的路径。 并行区域的词法范围之外遇到指令称为孤立的指令。

没有隐式的屏障并行区域的末尾。 只有团队的主线程继续执行并行区域的末尾。

如果团队执行并行区域中的线程遇到其他并行构造，它会创建一个新的团队，并成为该新团队的主节点。 默认情况下，嵌套并行区域进行序列化。 因此，默认情况下，嵌套并行区域执行由团队组成一个线程。 通过使用运行时库函数可能会更改默认行为`omp_set_nested`环境变量或`OMP_NESTED`。 但是，在团队中执行嵌套并行区域的线程数是实现定义的。

限制`parallel`指令如下所示：

- 最多一个`if`子句可以出现在指令中。

- 它具有未指定是否任何副作用 if 表达式或`num_threads`表达式出现。

- 一个`throw`执行并行区域必须在使执行相同的结构化块的动态范围之内恢复并且它必须由同一个线程引发了异常捕获。

- 只有一个`num_threads`子句可以出现在指令中。 `num_threads`表达式计算上下文之外的并行区域，并计算结果必须为正整数值。

- 计算顺序`if`和`num_threads`子句未指定。

### <a name="cross-references"></a>交叉引用

- `private``firstprivate`， `default`， `shared`， `copyin`，并`reduction`子句 ([部分 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)库函数
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)环境变量
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) function
- [OMP_NESTED](4-environment-variables.md#44-omp_nested)环境变量
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)库函数

## <a name="24-work-sharing-constructs"></a>2.4 工作共享构造

工作共享构造分布情况下遇到此团队的成员相关联的语句的执行。 工作共享指令不启动新线程，并且在进入工作共享构造没有不存在任何隐式的障碍。

一系列工作共享构造和`barrier`遇到指令必须为团队中每个线程相同。

OpenMP 定义以下工作共享构造，并在后面的部分中介绍这些构造：

- [有关](#241-for-construct)指令
- [部分](#242-sections-construct)指令
- [单个](#243-single-construct)指令

### <a name="241-for-construct"></a>2.4.1 for 构造

`for`指令标识的指定将并行执行的相关联的循环迭代的迭代工作共享构造。 迭代的`for`循环分布在线程中执行绑定到并行构造团队已经存在。 语法`for`构造如下所示：

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

子句是以下值之一：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

`for`指令的相应结构上放置限制`for`循环。 具体而言，在相应`for`循环必须具有规范形状：

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
一个有符号的整数的变量。 如果此变量将否则共享，它隐式设为私有的持续时间内`for`。 请不要修改此变量的主体内`for`语句。 除非另有指定变量`lastprivate`之后循环是不确定, 其值。

*logical-op*<br/>
以下项之一：

- `<`
- `<=`
- `>`
- `>=`

*lb*， *b*，和*incr*<br>
循环固定的整数表达式。 没有这些表达式的计算期间同步使任何计算的方面的副作用产生不确定的结果。

规范格式允许数量的循环迭代将在进入循环进行计算。 使用中的类型的值进行此计算*var*之后整型提升。 特别地，如果值为*b* `-` *lb* `+` *incr* ，结果是不确定的类型，不能表示。 此外，如果*逻辑操作*是`<`或`<=`，然后*incr expr*必须导致*var*以提高在每个循环迭代。   如果*逻辑操作*是`>`或`>=`，然后*incr expr*必须导致*var*循环的每个迭代上获取较小。

`schedule`子句指定如何迭代的`for`循环分别位于若干个团队的线程。 程序的正确性必须不依赖于哪些线程执行的特定小版本。 值*使用 chunk_size*，如果指定，必须用正值是循环固定的整数表达式。 没有此表达式的计算期间同步使任何计算的方面的副作用产生不确定的结果。 计划*种类*可以是下列值之一：

表 2-1:`schedule`子句*种类*值

|||
|-|-|
|静态|当`schedule(static,`*使用 chunk_size* `)`迭代被分到指定的大小的区块的指定*使用 chunk_size*。 区块以静态方式分配给团队以轮循机制方式按线程号顺序中的线程。 如果未 *使用 chunk_size* 迭代空间划分为与分配给每个线程一个区块的大小，大致相等的块的指定。|
|dynamic|当`schedule(dynamic,`*使用 chunk_size* `)`迭代划分为区块，每个包含的一系列的指定*使用 chunk_size*迭代。 每个区块被分配给正在等待分配一个线程。 线程执行迭代的区块，并等待其下一步的分配，没有块保持可以被指定。 要分配的最后一个块区可能具有较小数目的迭代。 如果未*使用 chunk_size*指定，则默认为 1。|
|引导式|当`schedule(guided,`*使用 chunk_size* `)`迭代分配与减小大小的区块中的线程的指定。 当线程完成其已分配的块的迭代时，它具有动态分配另一个区块，直到 none 离开。 有关 *使用 chunk_size*的每个块区大小为 1，是大约未分配的线程数除以的迭代数。 这些大小几乎按指数规律减小到 1。 有关*使用 chunk_size*值*k*大于 1，大小为几乎呈指数级减少*k*，但最后一个区块可能有较少的比*k*迭代。 如果未*使用 chunk_size*指定，则默认为 1。|
|Runtime — 运行时|当`schedule(runtime)`指定，则有关计划被延迟到运行时的决定。 计划*种类*可以通过设置环境变量在运行时选择的消息块的大小和`OMP_SCHEDULE`。 如果未设置此环境变量，生成的计划是实现定义的。 当`schedule(runtime)`指定，则*使用 chunk_size*不能指定。|

在没有显式定义`schedule`子句，则默认`schedule`是实现定义的。

OpenMP 兼容的程序不应依赖于正确的执行的特定计划。 程序不应依赖于计划*种类*精确地符合更高版本，提供的说明，因为它是可以使位于同一个计划的实现中的变体*种类*跨不同的编译器。 描述可以用于选择适合于特定的情况的计划。

`ordered`子句必须存在何时`ordered`指令将绑定到`for`构造。

末尾没有隐式屏障`for`构造，除非`nowait`指定子句。

限制`for`指令如下所示：

- `for`循环必须是结构化的块中，并且，此外，其执行必须未终止的`break`语句。

- 循环的值控制的表达式`for`与相关联的循环`for`指令必须是相同的团队中的所有线程。

- `for`循环迭代变量必须具有带符号的整数类型。

- 只有一个`schedule`子句中显示的`for`指令。

- 只有一个`ordered`子句中显示的`for`指令。

- 只有一个`nowait`子句中显示的`for`指令。

- 它是未指定的 if 或任何一侧效果内的何种频率*使用 chunk_size*， *lb*， *b*，或者*incr*表达式发生。

- 值*使用 chunk_size*表达式必须是相同的团队中的所有线程。

#### <a name="cross-references"></a>交叉引用

- `private``firstprivate`， `lastprivate`，并`reduction`子句 ([部分 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)环境变量
- [按序](#266-ordered-construct)构造
- [计划](d-using-the-schedule-clause.md)子句

### <a name="242-sections-construct"></a>2.4.2 部分构造

`sections`指令标识一个 noniterative 工作共享构造，它指定一组要在团队中的线程之间划分的构造。 每个部分由团队中的线程执行一次。 语法`sections`指令是按如下所示：

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

子句是以下值之一：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

每个部分的前面有`section`指令，尽管`section`指令是可选的第一个部分。 `section`指令必须出现在的词法范围内`sections`指令。 末尾没有隐式屏障`sections`构造，除非`nowait`指定。

限制`sections`指令如下所示：

- 一个`section`之外的词法范围不能出现指令`sections`指令。

- 只有一个`nowait`子句中显示的`sections`指令。

#### <a name="cross-references"></a>交叉引用

- `private``firstprivate`， `lastprivate`，并`reduction`子句 ([部分 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 single 构造

`single`指令标识一个构造，它指定由团队 （不一定是主线程） 中只有一个线程执行相关联的结构化的块。 语法`single`指令是按如下所示：

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

子句是以下值之一：

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `copyprivate(` *variable-list* `)`
- `nowait`

没有后的隐式屏障`single`构造，除非`nowait`指定子句。

限制`single`指令如下所示：

- 只有一个`nowait`子句中显示的`single`指令。
- `copyprivate`子句必须不能与`nowait`子句。

#### <a name="cross-references"></a>交叉引用

- `private``firstprivate`，并`copyprivate`子句 ([部分 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 组合的并行工作共享构造

组合的并行工作共享构造是用于指定并行区域具有只有一个工作共享构造的快捷方式。 这些指令的语义是与显式指定`parallel`指令后跟 single 的工作共享构造。

以下部分介绍了组合并行工作共享构造：

- [有关并行](#251-parallel-for-construct)指令
- [并行部分](#252-parallel-sections-construct)指令

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for 构造

`parallel for`指令是一种快捷方式`parallel`仅包含单个区域`for`指令。 语法`parallel for`指令是按如下所示：

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

此指令允许的所有子句`parallel`指令与`for`指令，除`nowait`子句，使用相同的含义和限制。 都与显式指定相同的语义`parallel`指令后面紧跟`for`指令。

#### <a name="cross-references"></a>交叉引用

- [并行](#23-parallel-construct)指令
- [有关](#241-for-construct)指令
- [数据特性子句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 并行段构造

`parallel sections`指令提供用于指定快捷窗体`parallel`具有只有一个区域`sections`指令。 都与显式指定相同的语义`parallel`指令后面紧跟`sections`指令。 语法`parallel sections`指令是按如下所示：

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*子句*可以是一个接受的子句`parallel`并`sections`指令，除`nowait`子句。

#### <a name="cross-references"></a>交叉引用

- [并行](#23-parallel-construct)指令
- [部分](#242-sections-construct)指令

## <a name="26-master-and-synchronization-directives"></a>2.6 Master 和同步指令

以下部分介绍：

- [主](#261-master-construct)构造
- [关键](#262-critical-construct)构造
- [屏障](#263-barrier-directive)指令
- [原子](#264-atomic-construct)构造
- [刷新](#265-flush-directive)指令
- [按序](#266-ordered-construct)构造

### <a name="261-master-construct"></a>2.6.1 master 构造

`master`指令标识一个构造，它指定由团队的主线程执行的结构化的块。 语法`master`指令是按如下所示：

```cpp
#pragma omp master new-linestructured-block
```

团队中的其他线程不执行关联的结构化的块。 没有任何隐式的屏障进入或退出 master 构造上。

### <a name="262-critical-construct"></a>2.6.2 critical 构造

`critical`指令标识相关联的结构化块执行一个线程限制一次的构造。 语法`critical`指令是按如下所示：

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

一个可选*名称*可能用于标识的关键区域。 标识符用于标识的关键区域具有外部链接，在独立于使用的标签、 标记、 成员和普通标识符的命名空间的命名空间中。

关键区域的开始处的一个线程等待，直到没有其他线程执行 （任意位置中程序） 具有相同名称的一个关键区域。 所有未命名`critical`指令将映射到相同的未指定名称。

### <a name="263-barrier-directive"></a>2.6.3 barrier 指令

`barrier`指令会同步在团队中的所有线程。 当遇到，团队中的每个线程等待，直到所有其他已达到此点。 语法`barrier`指令是按如下所示：

```cpp
#pragma omp barrier new-line
```

团队中的所有线程都遇到屏障后，团队中的每个线程开始后的屏障指令中并行执行的语句。 因为`barrier`指令不具有 C 语言语句作为其语法的一部分，有一些限制其放置在程序中。 有关正式的语法的详细信息，请参阅[附录 C](c-openmp-c-and-cpp-grammar.md)。下面的示例说明了这些限制。

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

### <a name="264-atomic-construct"></a>2.6.4 atomic 构造

`atomic`指令可确保特定的内存位置，而不是将其公开都会向可能的多个以原子方式，更新同时编写线程。 语法`atomic`指令是按如下所示：

```cpp
#pragma omp atomic new-lineexpression-stmt
```

表达式语句必须具有以下形式之一：

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

在前面的表达式：

- *x*是具有标量类型的左值表达式。

- *expr*是与标量类型的表达式，它不引用指定的对象*x*。

- *binop*不可重载的运算符，且具有之一`+`， `*`， `-`， `/`， `&`， `^`， `|`， `<<`，或`>>`。

尽管它是实现定义的实现是否替换所有`atomic`指令与`critical`指令必须具有相同唯一*名称*，则`atomic`指令允许更好地优化. 提供了硬件说明通常可以执行系统开销最少的原子更新。

负载和指定的对象的应用商店*x*是原子; 的计算*expr*不是原子事务。 若要避免出现争用情况，并行中的位置的所有更新应都保护与`atomic`指令，除了那些已知可免费的争用条件。

限制`atomic`指令如下所示：

- 对在整个程序的存储位置 x 的所有原子引用需要具有兼容的类型。

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

`flush`指令，无论是显式还是暗示的保证，指定"跨线程"序列点的实现需要确保团队中的所有线程都具有某些对象 （在下面指定） 在内存中的一致视图。 这意味着，以前计算的表达式引用这些对象的已完成，随后的计算还未开始。 例如，编译器必须还原对象的值从注册到内存，而硬件可能需要刷新写入缓冲区内存并重新加载内存中的对象的值。

语法`flush`指令是按如下所示：

```cpp
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步的对象可以所有指定的变量，则这些变量可以指定可选*变量列表*。 如果指针是否位于*变量列表*，指针本身会刷新，不是对象指针将指向。

一个`flush`指令而无需*变量列表*将包括无法访问对象的所有共享的对象同步与自动存储持续时间。 (这是可能需要考虑更多的开销比`flush`与*变量列表*。)一个`flush`指令而无需*变量列表*默示针对以下指令：

- `barrier`
- 在进入和退出 `critical`
- 在进入和退出 `ordered`
- 在进入和退出 `parallel`
- 在退出时从 `for`
- 在退出时从 `sections`
- 在退出时从 `single`
- 在进入和退出 `parallel for`
- 在进入和退出 `parallel sections`

如果未隐含指令`nowait`子句。 应注意的是，`flush`指令未隐含任何以下：

- 在进入 `for`
- 在进入或退出 `master`
- 在进入 `sections`
- 在进入 `single`

访问具有可变限定类型的对象的值的引用的行为就好像`flush`指令指定在上一个序列点的对象。 修改具有可变限定类型的对象的值的引用的行为就好像`flush`指令指定该对象在后续序列点。

因为`flush`指令不具有 C 语言语句作为其语法的一部分，有一些限制其放置在程序中。 有关正式的语法的详细信息，请参阅[附录 C](c-openmp-c-and-cpp-grammar.md)。下面的示例说明了这些限制。

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

限制`flush`指令如下所示：

- 中指定的变量`flush`指令不能是引用类型。

### <a name="266-ordered-construct"></a>2.6.6 有序构造

结构化的块以下`ordered`迭代会执行顺序循环中的顺序执行指令。 语法`ordered`指令是按如下所示：

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered`指令必须是动态的范围内`for`或`parallel for`构造。 `for`或`parallel for`到指令`ordered`构造绑定必须具有`ordered`中所述指定子句[部分 2.4.1](#241-for-construct)。 在执行`for`或`parallel for`通过构造`ordered`子句，`ordered`构造将顺序执行循环中执行顺序严格执行。

限制`ordered`指令如下所示：

- 使用循环的迭代`for`构造必须不超过一次，执行相同的有序的指令，同时必须执行多个`ordered`指令。

## <a name="27-data-environment"></a>2.7 数据环境

本节介绍指令和多个子句，用于控制数据环境的并行区域，在执行期间，如下所示：

- 一个[threadprivate](#271-threadprivate-directive)指令提供旨在使文件范围、 命名空间范围或静态的块范围变量为线程本地。

- 要并行或工作共享构造的持续时间内控制变量的共享属性的指令只能指定子句中所述[部分 2.7.2](#272-data-sharing-attribute-clauses)。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指令

`threadprivate`指令使命名的文件范围、 命名空间范围或块范围静态变量中指定*变量列表*线程私有的。 *变量列表*是不具有不完整类型的变量的以逗号分隔列表。 语法`threadprivate`指令是按如下所示：

```cpp
#pragma omp threadprivate(variable-list) new-line
```

每个副本`threadprivate`变量初始化一次，未指定点在程序之前对该副本的第一个引用并按常规方式 （即，因为主控副本会在串行执行程序中初始化）。 请注意，如果在显式初始值设定项的引用对象的`threadprivate`在变量的副本的第一个引用之前修改变量和对象的值，则行为是未指定。

因为与任何私有变量，一个线程不能引用另一个线程份`threadprivate`对象。 在序列区域和程序的主区域中，引用将会为对象的主线程的副本。

执行的第一个并行区域中的数据后`threadprivate`对象保证能够持久保留只有如果动态线程机制已被禁用，并且线程数保持不变的所有并行区域。

对限制`threadprivate`指令如下所示：

- 一个`threadprivate`文件范围或命名空间范围变量的指令必须出现之外的任何定义或声明中，并且必须从词法上位于其列表中之前对任何变量的所有引用。

- 在每个变量*变量列表*的`threadprivate`在词法上位于该指令的文件或命名空间范围内的变量声明必须引用在文件或命名空间范围内的指令。

- 一个`threadprivate`静态块范围变量的指令必须出现在变量的作用域并不在嵌套作用域。 指令从词法上必须位于所有引用的任何变量都之前在其列表中。

- 在每个变量*变量列表*的`threadprivate`块范围中的指令必须引用在词法上位于该指令之前的相同作用域中的变量声明。 变量声明必须使用静态存储类说明符。

- 如果在指定的变量`threadprivate`指令在一个翻译单元中，它必须以指定`threadprivate`指令在其中声明每个翻译单元中。

- 一个`threadprivate`变量必须出现在除任何子句`copyin`， `copyprivate`， `schedule`， `num_threads`，或`if`子句。

- 地址`threadprivate`变量不是地址常量。

- 一个`threadprivate`变量不能是不完整类型或引用类型。

- 一个`threadprivate`与非 POD 类类型的变量必须具有可访问的、 明确的复制构造函数，如果它用显式初始值设定项声明。

下面的示例演示如何修改显示在初始值设定项中的变量可能会导致未指定的行为，以及如何通过使用一个辅助对象和复制构造函数来避免此问题。

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

多个指令接受允许用户控制区域的持续时间内的变量的共享属性的子句。 共享特性子句仅适用于出现子句的指令的词法范围中的变量。 并非所有以下子句允许使用所有指令。 在指令中有所描述有效的特定指令的子句的列表。

如果变量是可见时并行或遇到工作共享构造，并且不共享特性子句中指定的变量或`threadprivate`指令，然后变量共享的。 共享并行区域的动态范围内声明的静态变量。 堆分配的内存 (例如，使用`malloc()`用 C 或 c + + 或`new`c + + 中的运算符) 共享。 （指向此内存，但是，可以是私有或共享。）具有自动存储持续时间并行区域的动态范围内声明的变量是私有类型。

大部分子句接受*变量列表*参数，其是可见的变量的以逗号分隔的列表。 如果变量引用中的数据共享特性子句已从模板派生的类型和不没有给该变量在程序中的任何其他引用，该行为不确定。

在指令子句内出现的所有变量必须都是可见的。 子句中根据需要可能会重复，但可能在多个子句中，指定没有变量，只不过变量可以指定在这种`firstprivate`和一个`lastprivate`子句。

以下部分介绍了数据共享特性子句：

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private`子句声明变量的列表是专用于在团队中每个线程中的变量。 语法`private`子句如下所示：

```cpp
private(variable-list)
```

中指定的变量的行为`private`子句如下所示。 具有自动存储持续时间的新对象分配的构造。 大小和新对象的对齐方式取决于变量的类型。 这种分配发生一次为每个线程团队，并默认构造函数调用的类对象，如有必要;否则的初始值是不确定的。  变量所引用的原始对象具有不确定的值输入到构造时、 内动态构造，程度不进行修改和已在从构造退出时不确定的值。

中的指令的构造的词法范围内，变量引用新的专用对象分配的线程。

对限制`private`子句如下所示：

- 中指定的类类型的变量`private`子句必须具有一个可访问的、 明确的默认构造函数。

- 中指定的变量`private`子句不能`const`-限定类型，除非它具有类类型与`mutable`成员。

- 中指定的变量`private`子句不能是不完整类型或引用类型。

- 在出现的变量`reduction`子句`parallel`指令不能指定`private`绑定到并行构造的工作共享指令上的子句。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate`子句提供的提供的功能超集`private`子句。 语法`firstprivate`子句如下所示：

```cpp
firstprivate(variable-list)
```

中指定的变量*变量列表*有`private`子句语义，如中所述[部分 2.7.2.1](#2721-private)。 初始化或构造会发生像它每个线程，在构造的线程的执行前一次执行情况。 有关`firstprivate`并行构造的子句，新的私有对象的初始值是立即在遇到它的线程的并行构造之前存在的原始对象的值。 有关`firstprivate`工作共享构造的子句，每个线程都执行的工作共享构造的新私有对象的初始值是原始的那个线程遇到的时间点之前存在的对象的值工作共享构造。 此外，对于 c + + 对象，每个线程的新私有对象是从原始对象构造的副本。

对限制`firstprivate`子句如下所示：

- 中指定的变量`firstprivate`子句不能是不完整类型或引用类型。

- 指定为类类型的变量`firstprivate`必须具有可访问的、 明确的复制构造函数。

- 专用并行区域内或在中都出现的变量`reduction`子句`parallel`指令不能指定`firstprivate`绑定到并行构造的工作共享指令上的子句。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`子句提供的提供的功能超集`private`子句。 语法`lastprivate`子句如下所示：

```cpp
lastprivate(variable-list)
```

中指定的变量*变量列表*具有`private`子句语义。 当`lastprivate`标识的每个值的工作共享构造的指令上出现子句`lastprivate`从关联的循环中，或从词法上最后一个区域指令，按顺序最后一次迭代的变量分配给变量的原始对象。 不值分配到的最后一次迭代变量`for`或`parallel for`，或通过从词法上最后一部分`sections`或`parallel sections`指令之后构造, 具有不确定的值。 未分配的子对象后构造还具有不确定的值。

对限制`lastprivate`子句如下所示：

- 所有限制`private`应用。

- 指定为类类型的变量`lastprivate`必须具有可访问的、 明确的复制赋值运算符。

- 专用并行区域内或在中都出现的变量`reduction`子句`parallel`指令不能指定`lastprivate`绑定到并行构造的工作共享指令上的子句。

#### <a name="2724-shared"></a>2.7.2.4 shared

此子句共享中出现的变量*变量列表*在团队中的所有线程之间。 发生在团队内的所有线程都访问的相同存储区域`shared`变量。

语法`shared`子句如下所示：

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default`子句，则允许用户以影响变量的数据共享属性。 语法`default`子句如下所示：

```cpp
default(shared | none)
```

指定`default(shared)`等效于显式列出中的每个当前可见变量`shared`子句，除非它是`threadprivate`或`const`-限定。 在没有显式`default`的默认行为是相同的子句，如果`default(shared)`指定。

指定`default(none)`要求至少一个以下必须为每个引用到并行构造的词法范围中的变量，则返回 true:

- 该变量显式列出的一个构造，它包含该引用的数据共享特性子句中。

- 在并行构造声明变量。

- 该变量是`threadprivate`。

- 该变量`const`-限定的类型。

- 变量是为循环控制变量`for`紧随的循环`for`或`parallel for`指令和变量的引用将显示在循环中。

指定一个变量上`firstprivate`， `lastprivate`，或`reduction`括住指令子句在封闭上下文中将导致为变量的隐式引用。 此类隐式引用也是根据上面列出的要求。

只有一个`default`子句可指定`parallel`指令。

数据共享特性可以通过重写的变量的默认`private`， `firstprivate`， `lastprivate`， `reduction`，和`shared`子句，如下面的示例所示：

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

此子句中出现的标量变量上执行减少*变量列表*，使用运算符*op*。 语法`reduction`子句如下所示：

`reduction(` *op* `:` *variable-list* `)`

减少通常指定为具有以下形式之一的语句：

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* （除外减法）
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

其中：

*x*<br/>
指定在列表中的 reduction 变量之一。

*variable-list*<br/>
以逗号分隔的标量降低变量列表。

*expr*<br/>
具有不引用的标量类型的表达式*x*。

*op*<br/>
不是重载的运算符，但之一`+`， `*`， `-`， `&`， `^`， `|`， `&&`，或`||`。

*binop*<br/>
不是重载的运算符，但之一`+`， `*`， `-`， `&`， `^`，或`|`。

以下是一种`reduction`子句：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

该示例中所示，操作员可能被隐藏在函数调用。 用户应小心运算符中指定`reduction`子句与相匹配的缩减运算。

尽管的右操作数`||`运算符在此示例中没有任何副作用，它们允许使用，但应谨慎使用。 在此上下文中，不保证按顺序循环的执行过程中发生的副作用可能会并行执行期间发生。 由于执行迭代的顺序是不确定，可能出现这种差异。

运算符用来确定编译器用于减少任何私有变量的初始值和来确定终止运算符。 显式指定运算符允许减少语句要构造的词法范围之外。 任意数量的`reduction`子句可指定指令，但变量可能会出现在最多一个`reduction`该指令的子句。

在每个变量的私有副本*变量列表*创建，另一个用于每个线程，如同`private`已使用子句。 根据运算符初始化的私有副本 （请参阅下表）。

为其区域末尾`reduction`指定子句，原始对象更新以反映组合其原始值与使用指定的运算符的私有副本的最终值的结果。 减少运算符可以 （除外减）、 所有结合使用，编译器可以自由地重新关联的最终值的计算。 （减法减少的部分结果添加引号以形成的最终值。

第一个线程到达包含子句和减少计算完成前保持时，原始对象的值将成为不确定。  通常情况下，计算会构造; 结束时完成但是，如果`reduction`向其构造上使用子句`nowait`是还应用，原始对象的值保持不确定执行屏障同步以确保所有线程都完成才`reduction`子句。

下表列出了有效的运算符和其规范初始化值。 实际初始化值将为使用 reduction 变量的数据类型一致。

|运算符|初始化|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

对限制`reduction`子句如下所示：

- 中的变量的类型`reduction`子句必须是有效的 reduction 运算符，不同之处在于永远不会允许使用指针类型和引用类型。

- 中指定的变量`reduction`子句不能`const`-限定。

- 专用并行区域内或在中都出现的变量`reduction`子句`parallel`指令不能指定`reduction`绑定到并行构造的工作共享指令上的子句。

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

`copyin`子句提供了一种机制来将分配到相同的值`threadprivate`团队执行并行区域中的每个线程的变量。 对于每个变量中指定`copyin`复制子句，团队在主线程中变量的值，像是通过分配到并行区域的开始处的线程专用副本。 语法`copyin`子句如下所示：

```cpp

copyin(
variable-list
)
```

对限制`copyin`子句如下所示：

- 中指定的变量`copyin`子句必须具有可访问的、 明确的复制赋值运算符。

- 中指定的变量`copyin`子句必须`threadprivate`变量。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate`子句提供了一种机制来使用私有变量广播来自团队的成员的其他成员的值。 它是使用共享的变量值时提供此类共享的变量会很困难 （例如，在需要在每个级别的不同变量的递归） 的替代方法。 `copyprivate`子句仅可出现在`single`指令。

语法`copyprivate`子句如下所示：

```cpp

copyprivate(
variable-list
)
```

效果`copyprivate`其变量列表中的变量上的子句与关联的结构化块执行后会发生`single`构造，以及之前团队中的线程的任何已离开构造结束时的障碍。 然后，在团队中每个变量中的所有其他线程*变量列表*，该变量将成为使用相应的值定义 （像是通过赋值） 中执行构造的线程的变量的结构化块。

限制`copyprivate`子句如下所示：

- 中指定的变量`copyprivate`子句不能出现在`private`或`firstprivate`的相同子句`single`指令。

- 如果`single`指令与`copyprivate`并行区域的动态范围中遇到子句中指定的所有变量`copyprivate`子句必须是私有在封闭上下文中。

- 中指定的变量`copyprivate`子句必须具有可访问的明确复制赋值运算符。

## <a name="28-directive-binding"></a>2.8 指令绑定

动态指令的绑定必须遵守以下规则：

- `for`， `sections`， `single`， `master`，并`barrier`指令将绑定到动态封闭`parallel`，如果存在，而不考虑任何值`if`可能会显示上的子句指令。 如果当前正在执行没有并行区域，由团队组成仅在主线程执行指令。

- `ordered`指令将绑定到动态封闭`for`。

- `atomic`指令强制执行独占访问与`atomic`中所有线程，而不仅仅是当前团队的指令。

- `critical`指令强制执行独占访问与`critical`中所有线程，而不仅仅是当前团队的指令。

- 指令可以永远不会将绑定到最接近之外的任何指令动态封闭`parallel`。

## <a name="29-directive-nesting"></a>2.9 指令嵌套

动态指令的嵌套的必须遵守以下规则：

- 一个`parallel`动态地在另一个指令`parallel`逻辑上建立启用一个新的团队，由仅在当前线程，除非嵌套并行度。

- `for``sections`，并`single`绑定到相同的指令`parallel`不允许嵌套在每个其他。

- `critical` 不允许嵌套在每个其他具有相同名称的指令。 请注意此限制不足以防止死锁。

- `for``sections`，并`single`指令不允许在动态程度`critical`， `ordered`，和`master`如果指令将绑定到相同的区域`parallel`作为区域。

- `barrier` 指令不允许在动态程度`for`， `ordered`， `sections`， `single`， `master`，和`critical`如果指令将绑定到相同的区域`parallel`作为区域。

- `master` 指令不允许在动态程度`for`， `sections`，并`single`指令如果`master`指令将绑定到相同`parallel`作为工作共享指令。

- `ordered` 中的动态程度不允许使用指令`critical`如果指令将绑定到相同的区域`parallel`作为区域。

- 并行区域外执行时，还允许使用并行区域内动态执行时，允许任何指令。 当动态执行用户指定的并行区域外，指令仅在主线程所组成的团队执行。
