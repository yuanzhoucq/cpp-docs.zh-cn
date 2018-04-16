---
title: 从 Visual Basic 应用程序调用 DLL 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed99b0ebe41a8f1bc9684638fa74e18556dd51f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>从 Visual Basic 应用程序调用 DLL 函数
对于 Visual Basic 应用程序 （或 Pascal 或 Fortran 等其他语言中的应用程序） 可以调用 C/c + + DLL 中函数，必须使用正确的调用约定，而无需由编译器进行任何名称修饰导出函数。  
  
 `__stdcall`创建正确的调用约定的函数 （被调用的函数清理堆栈和从右到左传递的参数） 但以不同方式修饰函数名。 因此，当**__declspec （dllexport)**使用在 DLL 中导出的函数，在导出的修饰的名称。  
  
 `__stdcall`名称修饰的前缀以下划线 (_) 的符号名称，并追加具有符号 at 符号 (@) 字符后跟自变量列表 （所需的堆栈空间） 中的字节数。 因此，函数声明为：  
  
```  
int __stdcall func (int a, double b)  
```  
  
 修饰名为：  
  
```  
_func@12  
```  
  
 C 调用约定 (`__cdecl`) 修饰形式的名称`_func`。  
  
 若要获取修饰的名称，请使用[/映射](../build/reference/map-generate-mapfile.md)。 利用**__declspec （dllexport)**执行下列任务：  
  
-   如果该函数导出使用 C 调用约定 (**_cdecl**)，它会导出名称时抽出前导下划线 (_)。  
  
-   如果正在导出的函数不使用 C 调用约定 (例如， `__stdcall`)，它将导出的修饰的名称。  
  
 由于没有方法来重写堆栈清理发生的位置，你必须使用`__stdcall`。 若要取消修饰名称与`__stdcall`，你必须通过.def 文件的导出节中使用别名指定它们。 这是显示为以下函数声明的如下所示：  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 在。DEF 文件：  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 对于通过在 Visual Basic 中编写的程序中调用的 Dll，本主题中所示的别名技术需要在.def 文件中。 如果别名都是在 Visual Basic 程序中，则不需要使用在.def 文件中指定别名。 它可以在 Visual Basic 程序中完成，通过添加到的别名子句[Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)语句。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [导出 DLL 使用。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)