---
title: "编译器错误 C2070 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2070
dev_langs: C++
helpviewer_keywords: C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6509a154605e8aa7196e790d3d6edd39941d75d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2070"></a>编译器错误 C2070
type： 非法的 sizeof 操作数  
  
 [Sizeof](../../cpp/sizeof-operator.md)运算符要求表达式或类型的名称。  
  
 下面的示例生成 C2070:  
  
```  
// C2070.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(func);   // C2070  
}  
```  
  
 可能的解决方法：  
  
```  
// C2070b.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(a);  
}  
```