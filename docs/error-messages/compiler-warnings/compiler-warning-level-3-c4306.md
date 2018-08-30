---
title: 编译器警告 （等级 3） C4306 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4306
dev_langs:
- C++
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab5372213819375a6c1fec3cfc43970415b6486a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219989"
---
# <a name="compiler-warning-level-3-c4306"></a>编译器警告（等级 3）C4306

> '*标识符*： 从转换*type1*to*type2*更大的

标识符的类型强制转换为更大的指针。 未填充的新类型高位将用零填充。

此警告可能表示不需要的转换。 在生成的指针可能无效。