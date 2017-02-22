---
title: "编译器警告（等级 1）C4377 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4377"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4377"
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 1）C4377
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本机类型默认情况下为私有类型；\-d1PrivateNativeTypes 已被否决  
  
 在早期版本中，默认情况下程序集中的本机类型为公共类型，使用未证明的内部编译器选项 \(**\/d1PrivateNativeTypes**\) 可将其变为私有。  
  
 默认情况下，现在程序集中的所有类型（本机和 CLR）均为私有类型，因此不再需要 **\/d1PrivateNativeTypes**。  
  
## 示例  
 下面的示例生成 C4377。  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```