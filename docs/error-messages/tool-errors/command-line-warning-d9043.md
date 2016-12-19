---
title: "命令行警告 D9043 | Microsoft Docs"
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
  - "D9043"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9043"
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令行警告 D9043
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“compiler\_option”的值“warning\_level”无效；假定为“4999”；“代码分析”警告与警告等级无关  
  
## 示例  
 下面的示例生成 C9043。  
  
```  
// D9043.cpp  
// compile with: /analyze /w16001  
// D9043 warning expected  
int main() {}  
```