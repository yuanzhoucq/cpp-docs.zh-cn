---
title: "链接的类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "外部链接, 链接类型"
  - "内部链接, 链接的类型"
  - "链接 [C++], 无"
  - "链接 [C++], 类型"
  - "无链接"
  - "类型 [C++], 链接"
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 链接的类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对象和函数的名称在翻译单元间共享的方式称为链接。  这些名称可具有：  
  
-   内部链接，在这种情况下，它们仅引用其自己的翻译单元中的程序元素；不会将其与其他翻译单元共享。  
  
     另一个翻译单元中的相同名称可能引用不同的对象或类。  带内部链接的名称有时称为其翻译单元的本地名称。  
  
     带内部链接的名称的示例声明为：  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   外部链接，在这种情况下，它们可引用程序中任何翻译单元中的程序元素 \- 程序元素在各个翻译单元之间共享。  
  
     确保另一个翻译单元中的相同名称引用同一对象或类。  带外部链接的名称有时称为全局名称。  
  
     带外部链接的名称的示例声明为：  
  
    ```  
    extern int i;  
    ```  
  
-   无链接，在此情况下，它们引用唯一实体。  另一个范围内的相同名称无法引用同一对象。  示例是一个枚举。  （但请注意，可以在无链接的情况下传递指向对象的指针。  这使得该对象在其他翻译单元中可访问。）  
  
## 请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)