---
title: 导出 C 函数，以用于 C 或 c + + 语言可执行文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee1d572bbfaa31ac626bfeb2b6ed7f61604628c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367701"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>导出 C 函数以用于 C 或 C++ 语言可执行文件  
  
如果你想要从 C 语言或 c + + 语言模块访问，你应该使用用 c 语言编写的 DLL 中具有函数 **__cplusplus**预处理器宏，以确定哪种语言正在编译，然后再声明这些带 C 链接如果正在使用 c + + 语言模块中的函数。 如果你使用此技术，并提供适合您的 DLL 的头文件，这些函数可由 C 和 c + + 用户且进行任何更改。  
  
下面的代码演示 C 和 c + + 客户端应用程序可以使用的标头文件：  
  
```h  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
如果你需要链接到 c + + 可执行文件的 C 函数，并且函数声明标头文件未使用上面的技术，c + + 源文件中，执行以下操作来阻止编译器修饰 C 函数名：  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
-   [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)