---
title: "编译器警告（等级 4）C4365 | Microsoft Docs"
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
  - "C4365"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4365"
ms.assetid: af4b4191-bdfd-4dbb-8229-3ba4405df257
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4365
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“action”: 从“type\_1”转换到“type\_2”，有符号\/无符号不匹配  
  
 例如，尝试将无符号值转换为有符号值。  
  
 默认情况下，C4365 为关闭状态。有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 示例  
 下面的示例生成 C4365。  
  
```  
// C4365.cpp  
// compile with: /W4  
#pragma warning(default:4365)  
  
int f(int) { return 0; }  
void Test(size_t i) {}  
  
int main() {  
   unsigned int n = 10;  
   int o = 10;  
   n++;  
   f(n);   // C4365  
   f(o);   // OK  
  
   Test( -19 );   // C4365  
}  
```