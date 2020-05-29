---
title: 表达式计算器错误 CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195755"
---
# <a name="expression-evaluator-error-cxx0024"></a>表达式计算器错误 CXX0024

操作需要左值

为需要左值的操作指定的表达式的计算结果不是左值。

左值（因此调用，因为它显示在赋值语句的左侧）是引用内存位置的表达式。

例如，`buffer[count]` 是有效的左值，因为它指向特定的内存位置。 逻辑比较 `zed != 0` 不是有效的左值，因为它的计算结果为 TRUE 或 FALSE，而不是内存地址。

此错误与 CAN0024 相同。
