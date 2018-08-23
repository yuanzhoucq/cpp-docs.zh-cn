---
title: 编译器错误 C2410 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c2a2df0941130c4f2416806a05ce0378373eb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226429"
---
# <a name="compiler-error-c2410"></a>编译器错误 C2410
identifier: context 中的不明确的成员名称  
  
 该标识符是多个结构或在此上下文中的联合的成员。  
  
 导致错误操作数中使用的结构或联合的说明符。 结构或联合说明符是类型的标识符`struct`或`union`(`typedef`名称或与结构或联合所引用的类型相同的变量)。 该说明符必须是第一个的成员选择运算符 （.），以使用操作数的左的操作数。