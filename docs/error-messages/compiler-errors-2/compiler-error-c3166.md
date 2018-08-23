---
title: 编译器错误 C3166 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3166
dev_langs:
- C++
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1996da7bb937fd00a4283ad94a4885432a9d47a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247701"
---
# <a name="compiler-error-c3166"></a>编译器错误 C3166
指针： 不能将内部 __gc 指针指向的指针声明为 type 的成员  
  
编译器找到了无效的指针声明 (`__nogc`指向`__gc`指针。)。 
  
C3166 才可访问使用过时的编译器选项 **/clr:oldSyntax**。  
