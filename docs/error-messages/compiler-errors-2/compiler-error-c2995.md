---
title: "编译器错误 C2995 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2995
dev_langs:
- C++
helpviewer_keywords:
- C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5c47d0930be7518dbef7cafd24e3767892f8f378
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2995"></a>编译器错误 C2995
“function”：函数模板已经定义  
  
 确保模板类的每个成员函数只有一个定义。  
  
 以下示例生成 C2995：  
  
```  
// C2995.cpp  
// compile with: /c  
template <class T>  
void Test(T x){}  
  
template <class T> void Test(T x){}   // C2995  
template <class T> void Test2(T x){}   // OK  
```
