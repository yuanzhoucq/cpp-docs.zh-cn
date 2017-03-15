---
title: "编译器警告（等级 3）C4800 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4800"
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 3）C4800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 将值强制为布尔值“true”或“false”\(性能警告\)  
  
 在分配非 `bool` 值，或将此类值强迫到类型 `bool` 中时，将生成此警告。  通常，此消息是由于向 `bool` 变量分配 `int` 变量引起的，其中 `int` 变量仅包含 **true** 和 **false** 值，并可重新声明为 `bool` 类型。  如果您无法重写表达式以使用 `bool` 类型，则可以向该表达式中添加“`!=0`”，它可使表达式成为 `bool` 类型。  将表达式转换为 `bool` 类型不会禁用警告，这是特意设计的。  
  
 下面的示例生成 C4800：  
  
```  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // try..  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```