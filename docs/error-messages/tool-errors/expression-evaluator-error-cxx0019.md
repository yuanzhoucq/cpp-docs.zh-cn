---
title: 表达式计算器错误 CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397102"
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