---
title: "编译器警告（等级 4）C4255 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4255"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4255"
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 4）C4255
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 未给出函数原型: 将“\(\)”转换为“\(void\)”  
  
 编译器未找到函数参数的显式列表。  此警告仅适用于 C 编译器。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4255：  
  
```  
// C4255.c  
// compile with: /W4 /WX  
#pragma warning (default : 4255)  
  
void f()  { // C4255  
// try the following line instead  
//void f(void) {  
}  
  
int main(int argc, char *argv[]) {  
   f();  
}  
```