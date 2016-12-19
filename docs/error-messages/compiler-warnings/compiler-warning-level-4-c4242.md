---
title: "编译器警告（等级 4）C4242 | Microsoft Docs"
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
  - "C4242"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4242"
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4242
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 从“type1”转换到“type2”，可能丢失数据  
  
 类型不同。  此类型转换可能导致数据丢失。  编译器执行此类型转换。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 有关 C4242 的其他信息，请参见[常见编译器错误](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 下面的示例生成 C4242：  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```