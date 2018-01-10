---
title: "编译器错误 C2362 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2362
dev_langs: C++
helpviewer_keywords: C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 08d8c42a32caaee503b6b6b130b1bcd371c32fd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2362"></a>编译器错误 C2362
identifier 的初始化已通过转到标签跳过  
  
 使用编译时[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳转到标签防止标识符进行初始化。  
  
 不能跳过具有初始值设定项的声明，除非声明包含在一个块，它不输入，或对象变量已初始化。  
  
 下面的示例生成 C2326:  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 可能的解决方法：  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```