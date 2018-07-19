---
title: 编译器警告 （等级 1） C4549 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4549
dev_langs:
- C++
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a31a2aec4753cf0cd800ca22ea1e997a5929bf3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284324"
---
# <a name="compiler-warning-level-1-c4549"></a>编译器警告（等级 1）C4549
operator： 逗号不起任何作用; 前的运算符是否要使用 operator？  
  
 编译器检测到格式不正确逗号表达式。  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4549:  
  
```  
// C4549.cpp  
// compile with: /W1  
#pragma warning (default : 4549)  
  
int main() {  
   int i = 0, k = 0;  
  
   if ( i == 0, k )   // C4549  
   // try the following line instead  
   // if ( i == 0 )  
      i++;  
}  
```