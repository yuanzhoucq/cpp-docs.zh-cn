---
title: "编译器警告（等级 3）C4390 | Microsoft Docs"
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
  - "C4390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4390"
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“;”: 找到空的受控语句；是否有意这样使用?  
  
 在不包含任何指令的控制语句后找到了分号。  
  
 如果收到 C4390 是宏的缘故，则应使用 [warning](../../preprocessor/warning.md) 杂注在包含该宏的模块中禁用 C4390。  
  
 下面的示例生成 C4390：  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```