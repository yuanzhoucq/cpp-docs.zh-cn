---
title: "编译器错误 C2865 | Microsoft Docs"
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
  - "C2865"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2865"
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2865
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 对 handle\_or\_pointer 的非法比较  
  
 对于对 [类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md) 或 [\_\_gc](../../misc/gc.md) 类型的引用，仅可比较其相等性，以查看它们是引用同一对象 \(\=\=\) 还是引用不同的对象 \(\!\=\)。  
  
 无法比较它们的排序顺序，因为 .NET 运行时可能随时移动托管对象，从而改变该测试的结果。