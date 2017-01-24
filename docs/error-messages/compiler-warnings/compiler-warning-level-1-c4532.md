---
title: "编译器警告（等级 1）C4532 | Microsoft Docs"
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
  - "C4532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4532"
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“continue”: 在终止处理期间从 \_\_finally\/finally 块跳出的行为未定义  
  
 编译器遇到了下列关键字之一：  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 导致在不正常终止期间跳出 [\_\_finally](../../cpp/try-finally-statement.md) 或 [finally](../../dotnet/finally.md) 块。  
  
 如果发生异常，并且在终止处理程序（`__finally` 块或 finally 块）执行期间堆栈正在展开时，代码在 `__finally` 块结束之前跳出 `__finally` 块，则该行为是未定义的。  控制可能没有返回给展开的代码，因此可能没有正确处理该异常。  
  
 如果必须跳出 **\_\_finally** 块，请首先检查不正常终止。  
  
 下面的示例生成 C4532；只需注释掉跳转语句即可解决此警告。  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```