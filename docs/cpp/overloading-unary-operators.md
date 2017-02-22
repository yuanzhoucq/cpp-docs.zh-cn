---
title: "重载一元运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "增量运算符, 重载的"
  - "运算符 [C++], 一元的"
  - "加号运算符"
  - "指针取消引用运算符重载"
  - "可以重新定义的一元运算符"
  - "一元运算符"
  - "一元运算符, 减号"
  - "一元运算符, 加号"
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 重载一元运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可重载的一元运算符如下：  
  
1.  `!`（[逻辑“非”](../cpp/logical-negation-operator-exclpt.md)）  
  
2.  `&`（[取址](../cpp/address-of-operator-amp.md)）  
  
3.  `~`（[二进制反码](../cpp/one-s-complement-operator-tilde.md)）  
  
4.  `*`（[取消指针引用](../cpp/indirection-operator-star.md)）  
  
5.  `+`（[一元加](../cpp/additive-operators-plus-and.md)）  
  
6.  `-`（[一元求反](../cpp/additive-operators-plus-and.md)）  
  
7.  `++`（[递增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)）  
  
8.  `--`（[递减](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)）  
  
9. 转换运算符  
  
 后缀递增和递减运算符（`++` 和 **––**）在[递增和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)中单独处理。  
  
 转换运算符也将在单独的主题中进行讨论；请参阅[转换](../cpp/user-defined-type-conversions-cpp.md)。  
  
 以下规则适用于所有其他一元运算符。  若要将一元运算符函数声明为非静态成员，则必须用以下形式声明它：  
  
 `ret-type operator` `op` `()`  
  
 其中 `ret-type` 是返回类型，`op` 是上表中列出的运算符之一。  
  
 若要将一元运算符函数声明为全局函数，则必须用以下形式声明它：  
  
 `ret-type operator` `op` \(`arg` \)  
  
 其中 `ret-type` 和 `op` 如上所述用于成员运算符函数，`arg` 是要参与运算的类类型的参数。  
  
> [!NOTE]
>  一元运算符的返回类型没有限制。  例如，逻辑“非”\(`!`\) 返回整数值是合理的，但并非强制性的。  
  
## 请参阅  
 [运算符重载](../cpp/operator-overloading.md)