---
title: "编译器错误 C2530 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2530
dev_langs: C++
helpviewer_keywords: C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f9ea1b462f2e0b141bdc624d77f548f19c4b71a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2530"></a>编译器错误 C2530
identifier： 必须初始化引用  
  
 你必须初始化引用声明它时，除非它已被声明：  
  
-   使用关键字[extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
-   作为类、 结构或联合的成员 （和构造函数中初始化）。  
  
-   作为函数声明或定义中的参数。  
  
-   作为函数的返回类型。  
  
 下面的示例生成 C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```