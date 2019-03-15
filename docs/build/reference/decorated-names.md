---
title: 修饰名
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: 3fae232e6ca886195315002f4e65063d8a23ddc8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815413"
---
# <a name="decorated-names"></a>修饰名

C 和 C++ 程序中的函数、数据和对象均在内部由其修饰名表示。 一个*修饰名*是由编译器创建的对象、 数据或函数定义在编译期间已编码的字符串。 它记录名称以及调用约定、类型、函数参数和其他信息。 此名称修饰，也称为*名称重整*、 帮助链接器查找正确的函数和对象链接可执行文件时。

修饰的命名约定在各种版本的 Visual C++ 中有所不同，并且可能在不同的目标体系结构上也不同。 若要正确链接使用 Visual C++、C 和 C++ 创建的源文件，应使用相同的编译器工具集、标志和目标体系结构编译 DLL 和库。

##  <a name="Using"></a> 使用修饰名

通常情况下，无需知道修饰名也可编写已成功编译和链接的代码。 修饰名是编译器和链接器内部的实现详细信息。 通常，这些工具可以处理未修饰形式的名称。 但是，在向链接器和其他工具指定函数名时，有时则需要修饰名。 例如，若要匹配重载的 C++ 函数、命名空间成员、类构造函数、析构函数和特殊成员函数，则必须指定修饰名。 有关选项标志和其他需要修饰名的情形的详细信息，请参阅正在使用的工具和选项的相关文档。

如果你更改函数名、类、调用约定、返回类型或任何参数，则修饰名也会改变。 在这种情况下，你必须获取新的修饰名，并将其用于指定了修饰名的任何位置。

在链接到用其他编程语言编写的或使用其他编译器的代码时，名称修饰也很重要。 编译器不同，则使用名称修饰约定不同。 在可执行文件链接到用另一种语言编写的代码时，必须特别留意将导出和导入的名称与调用约定相匹配。 程序集语言代码必须使用 Visual C++ 修饰名和调用约定来链接到使用 Visual C++ 编写的源代码。

##  <a name="Format"></a> 修饰名的 c + + 格式

C + + 函数的修饰名包含以下信息：

- 函数名称。

- 函数所属的类（如果该函数为成员函数）。 这可能包括含有函数所属的类的类，等等。

- 函数所属的命名空间（如果该函数是命名空间的一部分）。

- 函数参数的类型。

- 调用约定。

- 函数的返回类型。

修饰名中编码有函数名和类名。 修饰名的其余部分是具有仅用于编译器和链接器的内部意义的代码。 以下示例介绍的是未修饰和修饰的 C++ 名称。

|未修饰名|修饰名|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

##  <a name="FormatC"></a> 修饰名的 C 格式

C 函数的修饰形式取决于其声明中使用的调用约定，如下表所示。 这也是在将 C++ 代码声明为具有 `extern "C"` 链接时使用的修饰格式。 默认调用约定是 `__cdecl`。 请注意，在 64 位环境中，不修饰函数。

|调用约定|字体效果|
|------------------------|----------------|
|`__cdecl`|前导下划线 (**_**)|
|`__stdcall`|前导下划线 (**_**) 和尾随 at 符号 (**\@**) 后跟十进制中的参数列表中的字节数|
|`__fastcall`|前导空格和尾随 at 符号 (**\@**) 后接一个十进制数字表示的参数列表中的字节数|
|`__vectorcall`|两个尾随 at 符号 (**\@\@**) 后接参数列表中的字节的十进制数字|

##  <a name="Viewing"></a> 查看修饰名

在编译包含数据、对象或者函数定义或原型的源文件之后，可以获取符号名称的修饰形式。 若要检查你的程序中的修饰名，可以使用以下方法之一：

#### <a name="to-use-a-listing-to-view-decorated-names"></a>若要使用列表查看修饰名

1. 通过编译包含数据、 对象或函数定义或原型的源文件生成列表[列出文件类型](fa-fa-listing-file.md)设置为包含源代码的程序集的编译器选项 (**/FAs**)。

   例如，输入`cl /c /FAs example.cpp`在开发人员命令提示符下，若要生成列表文件 example.asm。

2. 在生成的列表文件中，找到以 PUBLIC 开头、分号结尾且后接未修饰的数据或函数名的行。 PUBLIC 和分号之间的符号即为修饰名。

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>若要使用 DUMPBIN 查看修饰名

1. 若要查看.obj 或.lib 文件中的导出的符号，请输入`dumpbin /symbols``objfile`开发人员命令提示符处。

2. 若要查找符号的修饰形式，请查找括号中的未修饰名。 修饰的名位于同一行中后一个管道, (&#124;) 字符和未修饰名称的前面。

##  <a name="Undecorated"></a> 查看未修饰名

可以使用 undname.exe 将修饰名转换为其未修饰形式。 此示例演示其工作原理：

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)<br/>
[使用 extern 指定链接](../../cpp/using-extern-to-specify-linkage.md)
