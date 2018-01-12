---
title: "编译器错误 C2234 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2234
dev_langs: C++
helpviewer_keywords: C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 799a1c8fa420606228d1f129c11bb17b255c6ec4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2234"></a>编译器错误 C2234
name： 数组的引用是非法  
  
 因为不允许引用的指针，则数组的引用不可能。  
  
 下面的示例生成 C2234:  
  
```  
// C2234.cpp  
int main() {  
   int i = 0, j = 0, k = 0, l = 0;  
   int &array[4] = {i,j,k,l};   // C2234  
   int array2[4] = {i,j,k,l};   // OK  
}  
```