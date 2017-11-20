---
title: "编译器警告 （等级 1 和等级 4） C4700 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4700
dev_langs: C++
helpviewer_keywords: C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f41e519a9dbcff3cc5ad4b718003e5964bfc3e85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>编译器警告（等级 1 和等级 4）C4700
未初始化的局部变量 name，然后使用  
  
 使用本地变量*名称*事先未被分配一个值，这可能导致不可预知的结果。  
  
 下面的示例生成 C4700:  
  
```  
// C4700.cpp  
// compile with: /W1  
int main() {  
   int i;  
   return i;   // C4700  
}  
```  
  
 下[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)这是 4 级警告。  下面的示例生成 C4700:  
  
```  
// C4700b.cpp  
// compile with: /W4 /clr:safe /c  
using namespace System;  
int main() {  
   Int32^ bi;  
   return *bi;   // C4700  
}  
```