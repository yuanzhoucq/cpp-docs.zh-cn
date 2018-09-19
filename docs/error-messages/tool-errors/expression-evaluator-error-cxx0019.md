---
title: 表达式计算器错误 CXX0019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fba76b75c640917b3b99cd41500d682cb1b32f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031803"
---
# <a name="expression-evaluator-error-cxx0019"></a>表达式计算器错误 CXX0019

错误的类型转换

C 表达式计算器无法执行类型强制转换一样编写的。

此错误是与 CAN0019 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 指定的类型是未知的。

1. 没有太多级别指针类型。 例如，类型强制转换

    ```
    (char **)h_message
    ```

     不能对 C 表达式计算器进行评估。