---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180220"
---
# <a name="__declspec"></a>__declspec

**Microsoft 专用**

用于指定存储类信息的扩展特性语法使用 **__declspec**关键字，该关键字指定给定类型的实例将与下面列出的 Microsoft 特定存储类特性一起存储。 其他存储类修饰符的示例包括**static**和**extern**关键字。 但是，这些关键字是 C 和 C++ 语言的 ANSI 规范的一部分，并且本身不包含在扩展特性语法中。 扩展特性语法简化并标准化了 Microsoft 专用的 C 和 C ++ 语言扩展。

## <a name="grammar"></a>语法

*decl*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec （** *decl* **）**

extended-decl-modifier-seq：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;扩展*decl-修饰符* *decl*

extended-decl-modifier：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**对齐（** *#* **）**<br/>
&nbsp;allocate &nbsp;&nbsp;&nbsp; **（"** *segname* **"）**<br/>
&nbsp;**分配**器 &nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg （"** *segname* **"）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;不**推荐使用**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**过程**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**属性（** { **get =** _get_func_name_ &#124; **，put =** _put_func_name_ } **）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**限制**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre （nomitigation）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uuid （"** *ComObjectGUID* **"）**

空格用于分隔声明修饰符序列。 示例显示在后面的部分。

扩展属性语法支持以下特定于 Microsoft 的存储类特性： [align](../cpp/align-cpp.md)、 [allocate](../cpp/allocate.md)、[分配](../cpp/allocator.md)器、 [appdomain](../cpp/appdomain.md)、 [code_seg](../cpp/code-seg-declspec.md)、[弃用](../cpp/deprecated-cpp.md)、 [dllexport](../cpp/dllexport-dllimport.md)、 [dllimport](../cpp/dllexport-dllimport.md)、 [jitintrinsic](../cpp/jitintrinsic.md)、 [naked](../cpp/naked-cpp.md)、 [noalias](../cpp/noalias.md)、 [noinline](../cpp/noinline.md)、 [noreturn](../cpp/noreturn.md)、 [nothrow](../cpp/nothrow-cpp.md)、 [novtable](../cpp/novtable.md)、 [process](../cpp/process.md)、 [restrict](../cpp/restrict.md)、 [safebuffers](../cpp/safebuffers.md)、 [selectany](../cpp/selectany.md) [、spectre](../cpp/spectre.md)和[线程](../cpp/thread.md)。 它还支持以下 COM 对象属性： [property](../cpp/property-cpp.md)和[uuid](../cpp/uuid-cpp.md)。

**Code_seg**、 **dllexport**、 **dllimport**、 **naked**、 **noalias**、 **nothrow**、 **property**、 **restrict**、 **selectany**、 **thread**和**uuid**存储类特性仅为它们应用于的对象或函数的声明的属性。 **Thread**特性只影响数据和对象。 **Naked**和**spectre**特性仅影响函数。 **Dllimport**和**dllexport**特性影响函数、数据和对象。 **属性**、 **selectany**和**uuid**特性会影响 COM 对象。

为了与早期版本兼容， **_declspec**是 **__declspec**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

应将 **__declspec**关键字放在简单声明的开头。 编译器将忽略任何警告，位于 * 或 & 之后、在声明中的变量标识符前面的任何 **__declspec**关键字。

用户定义的类型声明的开头指定的 **__declspec**特性适用于该类型的变量。 例如：

```cpp
__declspec(dllimport) class X {} varX;
```

在本例中，此特性应用于 `varX`。 放置在**class**或**struct**关键字之后的 **__declspec**特性适用于用户定义的类型。 例如：

```cpp
class __declspec(dllimport) X {};
```

在本例中，此特性应用于 `X`。

使用简单声明的 **__declspec**属性的一般准则如下所示：

*decl-seq* *init-list*;

*Decl-seq*应包含一个基类型（例如**int**、 **float**、 **typedef**或类名）、一个存储类（例如， **static**、 **extern**）或 **__declspec**扩展插件。 *Init-声明符列表*应包含声明的指针部分。 例如：

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

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[C 扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)
