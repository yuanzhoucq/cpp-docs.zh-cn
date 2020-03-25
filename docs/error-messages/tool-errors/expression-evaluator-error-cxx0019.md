---
title: 表达式计算器错误 CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195885"
---
# <a name="expression-evaluator-error-cxx0019"></a>表达式计算器错误 CXX0019

错误的类型转换

C 表达式计算器无法按编写方式执行类型强制转换。

此错误与 CAN0019 相同。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 指定的类型未知。

1. 指针类型太多。 例如，类型转换

    ```
    (char **)h_message
    ```

   C 表达式计算器无法计算此值。
