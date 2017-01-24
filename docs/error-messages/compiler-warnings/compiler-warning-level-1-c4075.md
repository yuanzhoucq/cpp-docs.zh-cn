---
title: "编译器警告（等级 1） C4075 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4075"
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1） C4075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始值设定项放置在无法识别的初始化区域中  
  
 [\#pragma init\_seg](../../preprocessor/init-seg.md) 使用无法识别的节名称。 编译器忽略 **pragma** 命令。  
  
 以下示例生成 C4075：  
  
```  
// C4075.cpp // compile with: /W1 #pragma init_seg("mysegg")   // C4075 // try.. // #pragma init_seg(user) int main() { }  
```