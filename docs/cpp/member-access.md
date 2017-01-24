---
title: "成员访问 | Microsoft Docs"
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
  - "成员访问, 重载运算符"
  - "成员选择运算符"
  - "运算符重载, 成员访问运算符"
  - "指针, 智能"
  - "智能指针"
  - "智能指针, 定义"
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 成员访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类成员访问可通过重载成员访问运算符 \(**–\>**\) 来控制。  此运算符被视为此用法中的一元运算符，而重载运算符函数必须是类成员函数。  因此，此类函数的声明是：  
  
## 语法  
  
```  
  
class-type *operator–>()  
```  
  
## 备注  
 其中，*class\-type* 是此运算符所属的类的名称。  成员访问运算符函数必须是非静态成员函数。  
  
 此运算符（通常与指针取消引用运算符一起使用）用于实现在取消引用用法或对用法计数前验证指针的“智能指针”。  
  
 无法重载 **.** 成员访问运算符。  
  
## 请参阅  
 [运算符重载](../cpp/operator-overloading.md)