---
title: 从 Visual Basic 应用程序调用 DLL 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1cedafaea33ac642e3a5593468b996f2442bd50
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894559"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>从 Visual Basic 应用程序调用 DLL 函数

对于 Visual Basic 应用程序 （或 Pascal 或 Fortran 等其他语言中的应用程序） 在 C/c + + DLL 中调用函数，函数必须使用导出正确的调用约定而无需由编译器进行任何名称修饰

`__stdcall` 创建正确的函数的调用约定 （被调用的函数清理堆栈和从右到左传递的参数），但以不同的方式修饰函数名。 因此，当 **__declspec （dllexport)** 使用在 DLL 中导出的函数，修饰的名被导出。

`__stdcall`名称修饰用下划线 (_) 作为符号名的前缀，并追加的符号宽度 at 符号 (**\@**) 字符后跟在参数列表 （所需的堆栈空间） 中的字节数。 因此，函数声明为：

```C
int __stdcall func (int a, double b)
```

修饰名为`_func@12`输出中。

C 调用约定 (`__cdecl`) 将作为该名称修饰`_func`。

若要获取修饰的名，请使用[/map](../build/reference/map-generate-mapfile.md)。 利用 **__declspec （dllexport)** 执行以下操作：

- 如果使用 C 调用约定导出函数 (**_cdecl**)，它会导出名称时抽出前导下划线 (_)。

- 如果要导出的函数不使用 C 调用约定 (例如， `__stdcall`)，它导出修饰的名。

由于没有办法重写堆栈清理发生的位置，必须使用`__stdcall`。 若要取消修饰名称与`__stdcall`，必须使用别名.def 文件的 EXPORTS 节中指定它们。 这一点，如下所示的以下函数声明：

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

在。DEF 文件：

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

对于通过在 Visual Basic 中编写的程序调用的 Dll，本主题中的别名技术需要.def 文件中。 如果在 Visual Basic 程序中完成了别名，不需要使用.def 文件中的别名。 它可以在 Visual Basic 程序中完成，通过添加到别名子句[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)语句。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [从 DLL 导出](../build/exporting-from-a-dll.md)

- [导出从 DLL 使用。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [导出 c + + 函数以用于 C 语言可执行文件](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)

- [修饰的名](../build/reference/decorated-names.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)
