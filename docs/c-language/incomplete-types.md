---
title: "不完整类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C], 不完整类型"
  - "不完整类型"
  - "结构, 不完整"
  - "类型 [C], 不完整"
  - "联合, 不完整"
  - "void 关键字 [C]"
  - "void 关键字 [C], 不完整"
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 不完整类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不完整类型是一种用于描述标识符但缺少确定该标识符的大小所需的信息的类型。  “不完整类型”可以是：  
  
-   您尚未指定其成员的结构类型。  
  
-   您尚未指定其成员的联合类型。  
  
-   您尚未指定其维度的数组类型。  
  
 void 类型是无法完成的不完整类型。  若要完成不完整类型，请指定缺少的信息。  以下示例演示如何创建和完成不完整类型。  
  
-   若要创建不完整的结构类型，请声明结构类型而不指定其成员。  在本例中，`ps` 指针指向称为 `student` 的不完整的结构类型。  
  
    ```  
    struct student *ps;  
    ```  
  
-   若要完成不完整的结构类型，请在稍后在指定其成员的同一范围中声明相同的结构类型，如下所示：  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   若要创建不完整的数组类型，请声明数组类型而不指定其重复计数。  例如：  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   若要完成不完整的数组类型，请在稍后在指定其重复计数的同一范围中声明相同的名称，如下所示：  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## 请参阅  
 [声明和类型](../c-language/declarations-and-types.md)