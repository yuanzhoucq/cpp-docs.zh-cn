---
title: "关于选择函数和宏的建议 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.functions
dev_langs: C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 810a4c2dbf5c80688dd739c48df0056ab394cafd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>关于选择函数和宏的建议
大多数 Microsoft 运行库例程都是编译的或汇编的函数，但有些例程是作为宏实现的。 当标头文件声明例程的函数和宏版本时，将优先考虑宏定义，因为它始终显示在函数声明之后。 在调用作为函数和宏实现的例程时，您可以通过两种方法强制编译器使用函数版本：  
  
-   将例程名称用括号括起来。  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   使用 `#undef` 指令“取消定义”宏：  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 如果您需要在库例程的函数和宏实现之间进行选择，请考虑以下折衷方案：  
  
-   **速度与大小** 使用宏的主要好处是执行速度更快。 在预处理期间，宏在被使用时将内联展开（由其定义替换）。 无论调用函数定义多少次，它仅执行一次。 宏可能会增加代码大小，但不会产生与函数调用关联的开销。  
  
-   **函数计算** 函数的计算结果为地址；而宏不是。 因此，您不能在需要指针的上下文中使用宏名称。 例如，您可以声明指向函数的指针而不是指向宏的指针。  
  
-   **类型检查** 在声明函数时，编译器会检查参数类型。 由于你不能声明宏，因此编译器无法检查宏自变量类型；尽管它可以检查传递给宏的自变量的数目。  
  
## <a name="see-also"></a>请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)