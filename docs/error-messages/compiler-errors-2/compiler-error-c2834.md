---
title: 编译器错误 C2834 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb4fb992f9213c4a4b456f786fd8f81308cec12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2834"></a>编译器错误 C2834
operator operator 必须是全局限定  
  
 `new`和`delete`运算符被绑定到类驻留的位置。 范围解析不能用于选择的版本`new`或`delete`从另一个类。 若要实现的多个窗体`new`或`delete`运算符，带有额外形参创建运算符的版本。