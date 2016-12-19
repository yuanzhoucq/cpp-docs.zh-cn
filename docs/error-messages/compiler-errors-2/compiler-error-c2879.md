---
title: "编译器错误 C2879 | Microsoft Docs"
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
  - "C2879"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2879"
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2879
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 只有现有命名空间才能由命名空间别名定义提供其他名称  
  
 不能将[命名空间别名](../../misc/namespace-alias.md)创建为命名空间以外的其他符号。  
  
 下面的示例生成 C2879：  
  
```  
// C2879.cpp  
int main() {  
   int i;  
   namespace A = i;   // C2879 i is not a namespace  
}  
```