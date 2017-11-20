---
title: "编译器警告 （等级 1） C4532 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4532
dev_langs: C++
helpviewer_keywords: C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cec2f70dfa6781c237cc1c08079904c7b48e171
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4532"></a>编译器警告（等级 1）C4532
continue: __finally/finally 块中的跳转出现不可确定的行为在终止处理过程  
  
 编译器遇到以下关键字之一：  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 导致外的跳转[__finally](../../cpp/try-finally-statement.md)或[最后](../../dotnet/finally.md)期间异常终止的块。  
  
 如果发生异常，以及时终止处理程序执行期间正在展开堆栈 (`__finally`或 finally 块)，和你的代码跳出`__finally`之前阻止`__finally`块结束，行为是不确定。 控件可能不返回到展开的代码，因此可能未正确处理异常。  
  
 如果您必须将跳过外**__finally**块中，首先检查异常终止。  
  
 下面的示例生成 C4532;只需注释掉跳转语句以解决此警告。  
  
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