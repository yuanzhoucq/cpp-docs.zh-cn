---
title: __declspec
ms.date: 10/09/2018
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: 3ee83203cc992ba8c5d05b7bb6974d3576baf59c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645089"
---
# <a name="declspec"></a>__declspec

**Microsoft 专用**

用于指定存储类信息使用的扩展的特性语法 **__declspec**关键字，这指定给定类型的实例是与下面列出特定于 Microsoft 的存储类特性一起存储。 其他存储类修饰符的示例包括**静态**并**extern**关键字。 但是，这些关键字是 C 和 C++ 语言的 ANSI 规范的一部分，并且本身不包含在扩展特性语法中。 扩展特性语法简化并标准化了 Microsoft 专用的 C 和 C ++ 语言扩展。

## <a name="grammar"></a>语法

*声明说明符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

extended-decl-modifier-seq：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

extended-decl-modifier：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**deprecated**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**process**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**

空格用于分隔声明修饰符序列。 示例显示在后面的部分。

扩展的特性语法支持这些特定于 Microsoft 的存储类特性：[对齐](../cpp/align-cpp.md)，[分配](../cpp/allocate.md)， [appdomain](../cpp/appdomain.md)， [code_seg](../cpp/code-seg-declspec.md)，[弃用](../cpp/deprecated-cpp.md)， [dllexport](../cpp/dllexport-dllimport.md)， [dllimport](../cpp/dllexport-dllimport.md)， [jitintrinsic](../cpp/jitintrinsic.md)，[裸](../cpp/naked-cpp.md)， [noalias](../cpp/noalias.md)， [noinline](../cpp/noinline.md)， [noreturn](../cpp/noreturn.md)， [nothrow](../cpp/nothrow-cpp.md)， [novtable](../cpp/novtable.md)[进程](../cpp/process.md)，[限制](../cpp/restrict.md)， [safebuffers](../cpp/safebuffers.md)， [selectany](../cpp/selectany.md)， [spectre](../cpp/spectre.md)，和[线程](../cpp/thread.md)。 它还支持这些 COM 对象属性：[属性](../cpp/property-cpp.md)并[uuid](../cpp/uuid-cpp.md)。

**Code_seg**， **dllexport**， **dllimport**，**裸**， **noalias**， **nothrow**，**属性**，**限制**， **selectany**，**线程**，和**uuid**存储类特性是仅的声明的函数应用于的对象的属性。 **线程**属性会影响数据仅和对象。 **裸**并**spectre**特性影响函数只能。 **Dllimport**并**dllexport**特性影响函数、 数据和对象。 **属性**， **selectany**，并**uuid**特性影响 COM 对象。

与以前版本的兼容性 **_declspec**是的同义词 **__declspec**除非编译器选项[/Za\(禁用语言扩展)](../build/reference/za-ze-disable-language-extensions.md)是指定。

**__Declspec**关键字应放置在简单声明的开头处。 编译器将忽略，而无需任何警告 **__declspec**关键字放在 * 或 & 和变量声明中标识符的前面。

一个 **__declspec**中用户定义的类型声明的开头指定特性应用于该类型的变量。 例如：

```cpp
__declspec(dllimport) class X {} varX;
```

在本例中，此特性应用于 `varX`。 一个 **__declspec**特性放置后**类**或**结构**关键字应用于用户定义类型。 例如：

```cpp
class __declspec(dllimport) X {};
```

在本例中，此特性应用于 `X`。

使用的一般准则 **__declspec**特性用于简单声明如下所示：

*声明说明符 seq* *init 声明符列表*;

*声明说明符 seq*应包含，除此之外，基类型 (例如**int**， **float**即**typedef**，或类名)、存储类 (例如**静态**， **extern**)，或 **__declspec**扩展。 *Init 声明符列表*应包含，除此之外，声明的指针部分。 例如：

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

以下代码声明了一个整数线程本地变量，并用一个值对其进行了初始化：

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)