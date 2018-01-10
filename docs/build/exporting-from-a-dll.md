---
title: "从 DLL 导出 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64571a0f648c0e33635990d9ca57744877429049
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll"></a>从 DLL 导出  
  
DLL 文件具有与.exe 文件，有一个重要的差异非常相似的布局-DLL 文件中包含的导出表。 导出表包含的每个 DLL 将导出到其他可执行文件的函数的名称。 这些函数是 DLL; 中的入口点可以通过其他可执行文件访问仅导出表中的函数。 DLL 中的任何其他函数是私有的 DLL。 可通过查看 DLL 导出表[DUMPBIN](../build/reference/dumpbin-reference.md)工具 /EXPORTS 选项。  
  
 你可以使用两种方法从 DLL 导出函数：  
  
-   创建一个模块定义 (.def) 文件和生成 DLL 时，使用.def 文件。 如果你想要使用此方法[序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  
  
-   使用关键字**__declspec （dllexport)**函数的定义中。  
  
 当使用任何一种方法导出函数，请确保使用[__stdcall](../cpp/stdcall.md)调用约定。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [使用.def 文件从 DLL 导出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [在 C 或 c + + 语言可执行文件中使用的导出 C 函数](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [按序号而不是按名称从 DLL 导出函数](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [确定要使用的链接方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [导入到应用程序](../build/importing-into-an-application.md)  
  
-   [导入和导出内联函数](../build/importing-and-exporting-inline-functions.md)  
  
-   [相互导入](../build/mutual-imports.md)  
  
## <a name="see-also"></a>请参阅  
 [导入和导出](../build/importing-and-exporting.md)