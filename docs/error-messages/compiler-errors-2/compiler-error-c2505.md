---
title: "编译器错误 C2505 | Microsoft Docs"
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
  - "C2505"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2505"
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2505
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”:“\_\_declspec\(modifer\)”只能应用于全局对象或静态数据成员的声明或定义  
  
 在函数中使用了被设计为仅在全局范围使用的 `__declspec` 修饰符。  
  
 有关更多信息，请参见 [appdomain](../../cpp/appdomain.md) 和[process](../../cpp/process.md)。  
  
 下面的示例生成 C2505：  
  
```  
// C2505.cpp  
// compile with: /clr  
  
// OK  
__declspec(process) int ii;  
__declspec(appdomain) int jj;  
  
int main() {  
   __declspec(process) int i;   // C2505  
   __declspec(appdomain) int j;   // C2505  
}  
```