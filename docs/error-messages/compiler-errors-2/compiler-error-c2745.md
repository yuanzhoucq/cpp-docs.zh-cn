---
title: "编译器错误 C2745 | Microsoft Docs"
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
  - "C2745"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2745"
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2745
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“token”: 该标记不能转换为标识符  
  
 标识符必须由合法字符组成。  
  
 下面的示例生成 C2745：  
  
```  
// C2745.cpp  
// compile with: /clr  
int main() {  
   int __identifier([));   // C2745  
}  
```