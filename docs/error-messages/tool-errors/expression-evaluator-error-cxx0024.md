---
title: 表达式计算器错误 CXX0024 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2816be7bb1d33757d9722d605d461ac6fb34fadd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118188"
---
# <a name="expression-evaluator-error-cxx0024"></a>表达式计算器错误 CXX0024

操作需要左值

要求左值的操作指定了计算结果不是左值的表达式。

左值 （因其将出现在赋值语句左侧而得名） 是指一个内存位置的表达式。

例如，`buffer[count]`是有效的左值，因为其指向特定内存位置。 逻辑比较`zed != 0`不是有效的左值，因为它为 TRUE 或 FALSE，计算结果不为内存地址。

此错误是与 CAN0024 相同。