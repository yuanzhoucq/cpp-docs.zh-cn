---
title: "编译器错误 C2081 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20f9f98ca03b9ed71d360b1b7c8bb64494a58416
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2081"></a>编译器错误 C2081
identifier： 形参列表非法中的名称  
  
 标识符导致语法错误。  
  
 可以通过使用旧样式的形式参数列表导致此错误。 你必须指定的正式参数的类型形参表中。  
  
 下面的示例生成 C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 可能的解决方法：  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```
