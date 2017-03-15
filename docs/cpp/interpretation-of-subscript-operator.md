---
title: "下标运算符的解释 | Microsoft Docs"
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
  - "数组 [C++], 下标 "
  - "解释下标运算符"
  - "运算符 [C++], 下标的解释"
  - "下标运算符, 解释"
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 下标运算符的解释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与其他运算符相似，下标运算符 \(**\[ \]**\) 也可由用户重新定义。  如果没有重载下标运算符，下标运算符的默认行为是使用以下方法组合数组名称和下标：  
  
 \*\(\(*array\-name*\) \+ \(*subscript*\)\)  
  
 像涉及指针类型的所有加法中一样，缩放将自动执行以调整类型的大小。  因此，生成的值不是来自 *array\-name* 的原点的 *subscript* 个字节，而是数组第 *subscript* 个元素。（有关此转换的详细信息，请参阅[相加运算符](../cpp/additive-operators-plus-and.md)。）  
  
 同样，对于多维数组，将使用以下方法获取地址：  
  
 **\(\(**   
 ***array\-name* \) \+ \(**   
 ***subscript* 1**  *max*2 *\* max*3*...max*n\)               **\+** *subscript*2 *\* max*3*...max*n\)                    . . .  *\+* *subscript*n\)\)  
  
## 请参阅  
 [数组](../cpp/arrays-cpp.md)