---
title: "导入和导出内联函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6f8d159a1537cdfee02d45805632ba9ad4afa7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting-inline-functions"></a>导入和导出内联函数
可以将导入的函数定义为内联。 效果大致是相同定义的标准函数内联;对函数的调用会展开为内联代码，类似于宏。 这是一种支持 c + + 类在 DLL 中某些成员函数以提高效率中可能内联主要有用。  
  
 导入的内联函数的一个功能是，你可以在 c + + 采用其地址。 编译器返回的副本驻留在 DLL 中的内联函数的地址。 导入的内联函数的另一个功能是可以在初始化静态本地数据的导入函数，与全局导入的数据不同。  
  
> [!CAUTION]
>  提供导入内联函数，因为他们可以创建的版本冲突的可能性时，应格外小心。 内联函数获取扩展到了应用程序代码中;因此，如果您更高版本重写函数，它未更新除非重新编译应用程序本身。 （通常，DLL 函数可以更新而重新生成的应用程序使用它们。）  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [从 DLL 导出](../build/exporting-from-a-dll.md)  
  
-   [从 DLL 使用导出。DEF 文件](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 从 DLL 导出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [导出和导入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [导出 C 语言可执行文件中使用的 c + + 函数](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [确定要使用的导出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [导入使用 __declspec （dllimport） 的应用程序](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>请参阅  
 [导入和导出](../build/importing-and-exporting.md)