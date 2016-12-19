---
title: "编译器警告（等级 4）C4514 | Microsoft Docs"
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
  - "C4514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4514"
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 未引用的内联函数已移除  
  
 优化程序移除了没有被调用的内联函数。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4514：  
  
```  
// C4514.cpp  
// compile with: /W4  
#pragma warning(default : 4514)  
class A  
{  
   public:  
      void func()   // C4514, remove the function to resolve  
      {  
      }  
};  
  
int main()  
{  
}  
```