---
title: "编译器警告（等级 4）C4207 | Microsoft Docs"
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
  - "C4207"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4207"
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4207
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 扩展初始值设定项窗体  
  
 在 Microsoft 扩展 \(\/Ze\) 下，可以在大括号内使用字符串来初始化未确定大小的 `char` 数组。  
  
## 示例  
  
```  
// C4207.c  
// compile with: /W4  
char c[] = { 'a', 'b', "cdefg" }; // C4207  
  
int main()  
{  
}  
```  
  
 此类初始化在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下无效。