---
title: "编译器错误 C2180 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2180
dev_langs: C++
helpviewer_keywords: C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdea36a8c6c7bf5e561c161dc7180ab3b563c0ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2180"></a>编译器错误 C2180
控制表达式具有类型“type”  
  
 `if`、`while`、`for` 或 `do` 语句中的控制表达式是强制转换为 `void` 的表达式。 若要解决此问题，请将控制表达式更改为生成 `bool` 的表达式或更改为可以转换为 `bool` 的类型。  
  
 以下示例生成 C2180：  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```