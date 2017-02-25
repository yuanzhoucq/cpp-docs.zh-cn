---
title: "关于选择函数和宏的建议 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.functions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数 [CRT], vs. 宏"
  - "宏, vs. 函数"
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 关于选择函数和宏的建议
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数 Microsoft 运行库类型库程序编译或汇编的函数，即，但有些例程实现作为宏。  在头文件声明函数和\/或例程的一个宏，该宏生成时定义，优先，因为在函数声明后总是它。  在调用实现作为函数和宏的例程时，可以按照两种方式强制编译器使用函数版本：  
  
-   用括号将定期名称。  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   “undefined”用 `#undef` 指令定义的宏：  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 如果您需要选择在函数类型库和程序中宏实现之间权衡，请看以下方案：  
  
-   使用**Speed versus size** 宏的主要好处是更快的执行时间。  在预处理期间，宏展开 \(替换按定义\) 是内联的，每次使用它。  函数只定义一次发生无论调用了多少次调用它。  宏可能会增加代码大小，但没有开销与函数调用。  
  
-   **Function evaluation** 函数计算结果为地址；宏不会。  因此不能在需要指针的上下文使用一个宏的名称。  例如，可以声明指针到函数，即，而不是指向宏。  
  
-   **Type\-checking**，在声明函数时，编译器可以检查参数类型。  由于不能声明宏，编译器无法检查该参数类型；虽然它可以检查参数的个数要传递到宏。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)