---
title: "模块定义 (。Def) 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 49f5eb5b75bad22b59cb4fbb98554bbfd44d13b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="module-definition-def-files"></a>模块定义 (.Def) 文件
模块定义 (.def) 文件提供有关导出、 属性和有关要链接的程序的其他信息的信息链接器。 .Def 文件生成 DLL 时最有用。 由于没有[链接器选项](../../build/reference/linker-options.md)，可以使用而不是模块定义语句.def 文件，则通常不需要。 你还可以使用[__declspec （dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md)作为一种方式指定导出的函数。  
  
 你可以在链接器阶段调用.def 文件[/DEF （指定模块定义文件）](../../build/reference/def-specify-module-definition-file.md)链接器选项。  
  
 如果要生成的.exe 文件，没有导出，使用.def 文件将使输出文件大且速度慢加载速度。  
  
 有关示例，请参阅[从 DLL 使用 DEF 文件导出](../../build/exporting-from-a-dll-using-def-files.md)。  
  
 请参阅以下各节，有关详细信息：  
  
-   [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [名称](../../build/reference/name-c-cpp.md)  
  
-   [部分](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [版本](../../build/reference/version-c-cpp.md)  
  
-   [保留的字](../../build/reference/reserved-words.md)  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [链接器选项](../../build/reference/linker-options.md)  