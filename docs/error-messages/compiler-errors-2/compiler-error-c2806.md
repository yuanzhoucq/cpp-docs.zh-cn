---
title: "编译器错误 C2806 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2806
dev_langs: C++
helpviewer_keywords: C2806
ms.assetid: 7c9ff1f4-1590-4c47-991d-b1075a173b48
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 272fbd789869387945fe8ad1a2177e182846ff89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2806"></a>编译器错误 C2806
operator operator 具有过多的正式参数  
  
 重载的运算符的参数太多。  
  
 下面的示例生成 C2806:  
  
```  
// C2806.cpp  
// compile with: /c  
class X {  
public:  
   X operator++ ( int, int );   // C2806 more than 1 parameter  
   X operator++ ( int );   // OK  
} ;  
```