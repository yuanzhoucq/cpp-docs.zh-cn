---
title: "编译器错误 C2513 | Microsoft Docs"
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
  - "C2513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2513"
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 在“\=”前没有声明变量  
  
 该类型说明符出现在声明中，但没有变量标识符。  
  
 下面的示例生成 C2513：  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 也可能由于为 Visual Studio .NET 2003 进行的编译器一致性工作生成此错误：不再允许 typedef 的初始化。  根据标准，不再允许 typedef 的初始化，并且现在将生成编译器错误。  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 另一个方法就是删除 `typedef` 以便通过聚合初始值设定项列表定义变量，但是由于这样会创建与该类型名称相同的变量并且会隐藏类型名称，因此并不建议使用此方法。