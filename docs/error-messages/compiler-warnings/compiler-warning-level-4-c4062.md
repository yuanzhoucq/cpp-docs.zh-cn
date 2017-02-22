---
title: "编译器警告（等级 4）C4062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4062"
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 4）C4062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未处理枚举“enumeration”的开关中的枚举器“identifier”  
  
 在 `switch` 语句中，枚举没有任何相关联的处理程序，并且没有任何**默认**标签。  
  
 默认情况下，此警告处于关闭状态。 请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)了解详细信息。  
  
 下面的示例生成 C4062：  
  
```  
// C4062.cpp // compile with: /W4 #pragma warning(default : 4062) enum E { a, b, c }; void func ( E e ) { switch(e) { case a: case b: break;   // no default label }   // C4062, enumerate 'c' not handled } int main() { }  
```