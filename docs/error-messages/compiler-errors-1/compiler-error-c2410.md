---
title: 编译器错误 C2410 |Microsoft Docs
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
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052447"
---
# <a name="compiler-error-c2410"></a>编译器错误 C2410

identifier: context 中的不明确的成员名称

标识符是多个结构或在此上下文中的联合的成员。

导致了错误的操作数上使用的结构或联合的说明符。 结构或联合说明符是类型的标识符`struct`或`union`(`typedef`名称或变量的结构或联合所引用的类型相同)。 该说明符必须是第一个的成员选择运算符 （.），若要使用的操作数的左的操作数。