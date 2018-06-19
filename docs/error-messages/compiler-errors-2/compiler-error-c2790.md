---
title: 编译器错误 C2790 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f1c90fed93666fad7513e2b4186a5baa2aa406
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232812"
---
# <a name="compiler-error-c2790"></a>编译器错误 C2790
super： 仅在类成员函数的主体内使用此关键字  
  
 如果用户曾经尝试使用关键字，则出现此错误消息[super](../../cpp/super.md)成员函数的上下文之外。  
  
 下面的示例生成 C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```