---
title: 从 Visual Basic 应用程序调用 DLL 函数
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 8d792dac45d69a0857bda551d1f3c03fc3d03d1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229878"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>从 Visual Basic 应用程序调用 DLL 函数

若要使 Visual Basic 应用程序（或诸如 Pascal 或 Fortran 等其他语言编写的应用程序）调用 C/C++ DLL 中的函数，必须使用正确的调用约定导出函数，而无需编译器进行任何名称修饰

`__stdcall` 为函数创建正确的调用约定（被调用的函数会清理堆栈，且参数从右向左传递），但以不同方式修饰函数名称。 因此，当对 DLL 中的已导出函数使用 `__declspec(dllexport)` 时，导出修饰名。

`__stdcall` 名称修饰使用下划线字符 (\_) 作为符号名称的前缀，并向符号追加 at 符号 (\@)，后跟参数列表中的字节数（所需堆栈空间）。 因此，在声明为以下内容时：

```C
int __stdcall func (int a, double b)
```

函数在输出中修饰为 `_func@12`。

C 调用约定 (`__cdecl`) 将名称修饰为 `_func`。

若要获取修饰名，请使用 [/MAP](reference/map-generate-mapfile.md)。 使用 `__declspec(dllexport)` 可以执行以下操作：

- 如果函数是使用 C 调用约定 (`__cdecl`) 导出的，则它会在导出名称时去掉前导下划线字符 (\_)。

- 如果导出的函数不使用 C 调用约定（例如 `__stdcall`），则它会导出修饰名。

因为无法替代发生堆栈清理的位置，所以必须使用 `__stdcall`。 若要使用 `__stdcall` 取消修饰名称，必须通过在 .def 文件的 EXPORTS 部分中使用别名来指定它们。 对于以下函数声明，这会显示如下：

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

在 .DEF 文件中：

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

若要使 Visual Basic 编写的程序可调用 DLL，.def 文件中需要本主题中所示的别名技术。 如果别名在 Visual Basic 程序中完成，则不需要在 .def 文件中使用别名。 可以通过将别名子句添加到 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) 语句，在 Visual Basic 程序中完成此操作。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [从 DLL 导出](exporting-from-a-dll.md)

- [使用 .DEF 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport) 从 DLL 导出](exporting-from-a-dll-using-declspec-dllexport.md)

- [导出 C++ 函数以用于 C 语言可执行文件](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](determining-which-exporting-method-to-use.md)

- [修饰名](reference/decorated-names.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
