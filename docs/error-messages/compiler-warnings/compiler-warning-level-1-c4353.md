---
title: "编译器警告（等级 1）C4353 | Microsoft Docs"
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
  - "C4353"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4353"
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4353
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展: 常数 0 作为函数表达式。请改用“\_\_noop”内部函数  
  
 不能将常数零 \(0\) 用作函数表达式。  有关更多信息，请参见 [\_\_noop](../../intrinsics/noop.md)。  
  
 下面的示例生成 C4353：  
  
```  
// C4353.cpp  
// compile with: /W1  
void MyPrintf(void){};  
#define X 0  
#if X  
   #define DBPRINT MyPrint  
#else  
   #define DBPRINT 0   // C4353 expected  
#endif  
int main(){  
DBPRINT();  
}  
```