---
title: "编译器警告（等级 4）C4431 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4431"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4431"
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 4）C4431
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

缺少类型说明符 \- 假定为 int。注意: C 不再支持默认的 int  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作可能导致此错误：Visual C\+\+ 不再创建默认为 int 的非类型化标识符。  必须显式指定标识符的类型。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 示例  
 下面的示例生成 C4431。  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```