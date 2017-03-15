---
title: "C++ 位域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "位域"
  - "位域"
  - "字段 [C++], bit"
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 位域
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类和结构可包含比整型类型占用更少存储空间的成员。  这些成员被指定为位域。  位域*成员声明符*规范的语法如下：  
  
## 语法  
  
```  
  
declarator  : constant-expression  
```  
  
## 备注  
 （可选）`declarator` 是在程序中访问成员的名称。  它必须是整型类型（包括枚举类型）。  *常数表达式*指定结构中成员所占据的位数。  匿名位域 — 即不带标识符的位域成员，可用于填充。  
  
> [!NOTE]
>  宽度为 0 的未命名位域强制将下一个位域与下一个 `type` 边界对齐，其中 `type` 是成员的类型。  
  
 下面的示例声明包含位域的结构：  
  
```  
// bit_fields1.cpp  
// compile with: /LD  
struct Date {  
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned short nMonth    : 5;    // 0..12  (5 bits)  
   unsigned short nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 `Date` 类型的对象的概念上的内存布局如下图所示。  
  
 ![Date 对象的内存布局](../cpp/media/vc38uq1.png "vc38UQ1")  
数据对象的内容布局  
  
 请注意，`nYear` 的长度为 8 位，并且会溢出声明类型 **unsigned short** 的字边界。  因此，它始于新 **unsigned short** 的开头。  并不必使所有位域均适合基础类型的对象；根据声明中请求的位数来分配新的存储单元。  
  
 **Microsoft 专用**  
  
 声明为位域的数据从低位到高位进行排序，如上图所示。  
  
 **结束 Microsoft 专用**  
  
 如果结构的声明包含长度为 0 的未命名字段（如以下示例所示），  
  
```  
// bit_fields2.cpp  
// compile with: /LD  
struct Date {  
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)  
   unsigned nMonthDay : 6;    // 0..31  (6 bits)  
   unsigned           : 0;    // Force alignment to next boundary.  
   unsigned nMonth    : 5;    // 0..12  (5 bits)  
   unsigned nYear     : 8;    // 0..100 (8 bits)  
};  
```  
  
 则内存布局如下图中所示。  
  
 ![带有零长度位域的 Date 对象的布局](../Image/vc38UQ2.png "vc38UQ2")  
带有零长度位域的数据对象的布局  
  
 位域的基础类型必须是整型类型，如[基本类型](../cpp/fundamental-types-cpp.md)中所述。  
  
## 位域的限制  
 以下列表详述了位域的错误操作：  
  
1.  采用位域的地址。  
  
2.  使用位域初始化引用。  
  
## 请参阅  
 [类和结构](../cpp/classes-and-structs-cpp.md)