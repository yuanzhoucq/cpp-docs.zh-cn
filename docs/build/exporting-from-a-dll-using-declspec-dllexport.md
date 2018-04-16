---
title: "从 DLL 使用 __declspec （dllexport） 导出 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dllexport
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51f20e47724a6d32dad014fbaf025cd283112c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>使用 __declspec(dllexport) 从 DLL 导出
Microsoft 引入**__export** Visual c + + 允许编译器自动生成的导出名称并将其放在.lib 文件中的 16 位编译器版本中。 此.lib 文件随后可静态.lib 一样将其与 DLL 链接。  
  
 在较新版本的编译器，你可以将导出数据、 函数、 类或类成员函数从 DLL 使用**__declspec （dllexport)**关键字。 **__declspec （dllexport)**将导出指令添加到对象文件中，因此不需要使用.def 文件。  
  
 当尝试导出修饰 c + + 函数名时，这种便利时最为明显。 由于没有对名称修饰没有标准规范，导出的函数的名称可能会更改不同的编译器版本。 如果你使用**__declspec （dllexport)**，重新编译的 DLL 和依赖的.exe 文件是仅向帐户的任何命名约定更改是必需的。  
  
 许多导出指令，如仅在.def 文件中，可以进行序号、 NONAME 和私有，并且没有办法可以指定不使用.def 文件的这些属性。 但是，使用**__declspec （dllexport)**除了使用.def 文件不会导致生成错误。  
  
 若要导出的函数， **__declspec （dllexport)**关键字必须出现左侧的调用约定关键字，如果指定一个关键字。 例如:  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 若要导出的所有公共数据成员和类中的成员函数，关键字必须出现左侧的类名称，如下所示：  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)`不能应用于具有函数`__clrcall`调用约定。  
  
 在生成您的 DLL 时，通常创建包含的函数原型和/或你要导出，然后添加的类的标头文件**__declspec （dllexport)**到标头文件中的声明。 若要使代码更具可读性，定义为宏**__declspec （dllexport)** ，将使用每个要导出的符号的宏：  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec （dllexport)**存储函数的 DLL 导出表中的名称。 如果你想要优化的表的大小，请参阅[从按序号而不是按名称的 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
> [!NOTE]
>  当移植到 Win32 DLL 源代码从 Win16 时，将每个实例**__export**与**__declspec （dllexport)**。  
  
 作为参考，搜索通过 Win32 Winbase.h 标头文件。 它包含的示例**__declspec （dllimport)**使用情况。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [__Declspec 关键字](../cpp/declspec.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)