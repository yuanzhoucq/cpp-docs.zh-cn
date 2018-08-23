---
title: __declspec |Microsoft Docs
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4358712e5573095229a48a6d08b78706c608874d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403643"
---
# <a name="declspec"></a>__declspec

**Microsoft 专用**

用于指定存储类信息使用的扩展的特性语法 **__declspec**关键字，这指定给定类型的实例是与下面列出特定于 Microsoft 的存储类特性一起存储。 其他存储类修饰符的示例包括**静态**并**extern**关键字。 但是，这些关键字是 C 和 C++ 语言的 ANSI 规范的一部分，并且本身不包含在扩展特性语法中。 扩展特性语法简化并标准化了 Microsoft 专用的 C 和 C ++ 语言扩展。

## <a name="grammar"></a>语法

*声明说明符*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

extended-decl-modifier-seq：  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

extended-decl-modifier：  
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**deprecated**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**process**  
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**thread**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

空格用于分隔声明修饰符序列。 示例显示在后面的部分。

扩展的特性语法支持这些特定于 Microsoft 的存储类特性：[对齐](../cpp/align-cpp.md)，[分配](../cpp/allocate.md)， [appdomain](../cpp/appdomain.md)， [code_seg](../cpp/code-seg-declspec.md)，[弃用](../cpp/deprecated-cpp.md)， [dllexport](../cpp/dllexport-dllimport.md)， [dllimport](../cpp/dllexport-dllimport.md)， [jitintrinsic](../cpp/jitintrinsic.md)，[裸](../cpp/naked-cpp.md)， [noalias](../cpp/noalias.md)， [noinline](../cpp/noinline.md)， [noreturn](../cpp/noreturn.md)， [nothrow](../cpp/nothrow-cpp.md)， [novtable](../cpp/novtable.md)[进程](../cpp/process.md)，[限制](../cpp/restrict.md)， [safebuffers](../cpp/safebuffers.md)， [selectany](../cpp/selectany.md)， [spectre](../cpp/spectre.md)，和[线程](../cpp/thread.md)。 它还支持这些 COM 对象属性：[属性](../cpp/property-cpp.md)并[uuid](../cpp/uuid-cpp.md)。

**Code_seg**， **dllexport**， **dllimport**，**裸**， **noalias**， **nothrow**，**属性**，**限制**， **selectany**，**线程**，和**uuid**存储类特性是仅的声明的函数应用于的对象的属性。 **线程**属性会影响数据仅和对象。 **裸**并**spectre**特性影响函数只能。 **Dllimport**并**dllexport**特性影响函数、 数据和对象。 **属性**， **selectany**，并**uuid**特性影响 COM 对象。

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
 [关键字](../cpp/keywords-cpp.md)  
 [C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)  