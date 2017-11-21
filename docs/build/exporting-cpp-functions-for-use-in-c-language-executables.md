---
title: "导出 c + + 函数以用于 C 语言可执行文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56e275b6c97bf319ab3d2bacb014423e6c0efd20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>导出 C++ 函数以用于 C 语言可执行文件  
  
如果你具有函数编写 c + + 中，你想要访问从 C 语言的模块，你应声明带 C 链接而不是 c + + 链接的这些函数的 DLL 中。 除非另行指定，则 c + + 编译器将使用 c + + 类型安全命名 （也称为名称修饰） 和 c + + 调用约定，可能很难从 C.调用  
  
若要指定 C 链接，指定`extern "C"`函数声明。 例如:   
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [修饰的名](../build/reference/decorated-names.md)  
  
-   [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>另请参阅  
 [从 DLL 导出](../build/exporting-from-a-dll.md)