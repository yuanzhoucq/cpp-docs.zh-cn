---
title: "编译器错误 C2464 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2464
dev_langs: C++
helpviewer_keywords: C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3992f1ecc19beb5c4fa1208fe82a93deab546260
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2464"></a>编译器错误 C2464
identifier： 不能使用 new 分配引用  
  
 引用标识符分配`new`运算符。 引用不是内存的对象，因此`new`无法返回指针指向它们。 使用标准的变量声明语法来声明引用。  
  
 下面的示例生成 C2464:  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```