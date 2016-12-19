---
title: "编译器警告（等级 1）C4630 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4630"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4630"
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4630
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”:“extern”存储类说明符在成员定义上非法  
  
 数据成员或成员函数被定义为 `extern`。  虽然整个对象可以是外部的，但成员不能是外部的。  编译器忽略了 `extern` 关键字。  下面的示例生成 C4630：  
  
```  
// C4630.cpp  
// compile with: /W1 /LD  
class A {  
   void func();  
};  
  
extern void A::func() {   // C4630, remove 'extern' to resolve  
}  
```