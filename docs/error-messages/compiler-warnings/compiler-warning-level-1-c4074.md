---
title: "编译器警告（等级 1）C4074 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4074"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4074"
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4074
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始值设定项放置在编译器保留的初始化区域中  
  
 由 [\#pragma init\_seg](../../preprocessor/init-seg.md) 指定的编译器初始化区域是为 Microsoft 保留的。  此区域中的代码可能会在 C 运行库的初始化之前执行。  
  
 下面的示例生成 C4074：  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```