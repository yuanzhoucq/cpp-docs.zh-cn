---
title: "C 浮点常量 | Microsoft Docs"
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
  - "常量, 浮点"
  - "双精度数据类型, 浮点常量"
  - "浮点常量"
  - "浮点常量, 关于浮点常量"
  - "浮点数字, 浮点常量"
  - "类型 [C], 常量"
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# C 浮点常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“浮点常数”是表示有符号的实数的十进制数字。  有符号的实数表示形式包括一个整数部分、一个小数部分和一个指数。  请使用浮点常数表示不能改变的的浮点值。  
  
## 语法  
 *浮点型常数*：  
 *小数\-常数 指数\-部分*  opt *浮动\-后缀* opt  
  
 *数字序列指数部分浮动后缀*  选择  
  
 *小数\-常数*：  
 *数字序列*  选择               **.**  *数字序列*  
  
 *数字序列*  **.**  
  
 *指数部分*：  
 **e**  *签名*  opt *数字序列*  
  
 **e**  *签名*  opt *数字序列*  
  
 *sign* ：一个  
 **\+ –**  
  
 *数字序列*:  
 *digit*  
  
 *数字序列数字*  
  
 *浮点后缀*：其中之一  
 **f l F L**  
  
 要么可以忽略小数点前面的数字（值的整数部分），要么忽略小数点后面的数字（小数部分），但不是两个都可以忽视。  仅在包含指数时才可忽略小数点。  空白字符不能分隔常量的数字或字符。  
  
 以下示例阐释了浮点常数和表达式的一些形式：  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 浮点型常数为正数的，除非它们在一个减号（**–**）前面。  在这种情况下，减号被视为一元算术求反运算符。  浮点型常数的类型有 **float**、**double**、`long double` 。  
  
 没有 **f**、**F**、**l** 的浮点常数或 **L** 后缀有类型 **double**。  如果字母 **f** 或 **F** 是后缀，该常数具有 **float**类型。  如果以字母 **l** 或 **L**作为后缀，其类型为 `long double`。  例如：  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 请注意 Microsoft C 编译器映射 **long double** 到类型 **double**。  有关类型 **double**, **float**, and **long** 的信息，请参见 [Storage of Basic Types](../c-language/storage-of-basic-types.md)（基本类型的存储）。  
  
 可以忽略浮点常数的整数部分，如以下示例所示。  Number .75 在以多种方法显示，其中包括：  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## 请参阅  
 [C 常量](../c-language/c-constants.md)