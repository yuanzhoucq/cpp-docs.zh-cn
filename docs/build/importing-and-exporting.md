---
title: 导入和导出 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee3ffe33dbb99f1f9b4124e2695d2e56dbe5544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368868"
---
# <a name="importing-and-exporting"></a>导入和导出
你可以将公共符号导入到应用程序或使用两种方法从 DLL 导出函数：  
  
-   生成 DLL 时使用的模块定义 (.def) 文件  
  
-   使用关键字 **__declspec （dllimport)** 或 **__declspec （dllexport)** 函数定义在主应用程序中  
  
## <a name="using-a-def-file"></a>使用.def 文件  
 模块定义 (.def) 文件是包含描述的 DLL 的各种属性的一个或多个模块语句的文本文件。 如果不使用 **__declspec （dllimport)** 或 **__declspec （dllexport)** 若要导出的 DLL 函数，DLL 要求的.def 文件。  
  
 你可以使用.def 文件复制到[导入应用程序](../build/importing-using-def-files.md)或[从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)。  
  
## <a name="using-declspec"></a>使用 __declspec  
 Visual c + + 使用 **__declspec （dllimport)** 和 **__declspec （dllexport)** 替换 **__export**以前在 16 位版本的 Visual c + + 中使用的关键字。  
  
 不需要使用 **__declspec （dllimport)** 为你的代码编译正确，但这样做允许编译器生成更好的代码。 编译器将能够生成更好的代码，因为它可以确定函数中是否存在 DLL 或不是，这使编译器能够生成跳过一定程度的间接性通常会出现跨 DLL 边界的函数调用中的代码。 但是，你必须使用 **__declspec （dllimport)** 导入在 DLL 中使用变量。  
  
 使用正确的.def 文件的导出部分中， **__declspec （dllexport)** 不是必需的。 **__declspec （dllexport)** 添加了来提供了简便的方法，以从.exe 或.dll 文件中导出函数，而无需使用.def 文件。  
  
 Win32 可移植可执行文件格式旨在最大程度减少必须接触修改导入的页面数。 若要执行此操作，它将调用导入地址表的一个位置中的任何程序的所有导入地址。 这样，加载程序以访问这些导入时修改只能将一个或两个页面。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [导入应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)