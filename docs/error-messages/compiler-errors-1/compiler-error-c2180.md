---
title: "编译器错误 C2180 | Microsoft Docs"
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
  - "C2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2180"
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2180
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制表达式具有类型“type”  
  
 `if`、`while`、`for` 或 `do` 语句中的控制表达式是强制转换为 `void` 的表达式。  若要解决此问题，请将控制表达式更改为生成 `bool` 的表达式或更改为可以转换为 `bool` 的类型。  
  
 以下示例生成 C2180：  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```