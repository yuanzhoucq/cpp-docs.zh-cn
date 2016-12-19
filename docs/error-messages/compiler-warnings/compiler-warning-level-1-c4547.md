---
title: "编译器警告（等级 1）C4547 | Microsoft Docs"
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
  - "C4547"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4547"
ms.assetid: 3edf1c2e-c0d5-444d-ae83-44a7cce24bb2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4547
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 逗号前的运算符无效；应输入带副作用的运算符  
  
 编译器检测到一个格式错误的逗号表达式。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4547：  
  
```  
// C4547.cpp  
// compile with: /W1  
#pragma warning (default : 4547)  
int i = 0;  
int j = 1;  
int main() {  
   int l = (i != i,0);   // C4547  
   // try the following line instead  
   // int l = (i != i);  
   // or  
   // int l = ((void)(i != i),0);  
}  
```