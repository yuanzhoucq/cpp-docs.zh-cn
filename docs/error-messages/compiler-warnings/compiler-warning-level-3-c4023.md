---
title: 编译器警告 （等级 3） C4023 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe457f9a6181fa11b34dd615ad4d5b9637c8bddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045167"
---
# <a name="compiler-warning-level-3-c4023"></a>编译器警告（等级 3）C4023

“symbol”：基指针传递到非原型函数：参数数目

将基指针传递给非原型函数会导致该指针被正常化，并产生不可预知的结果。

如果你使用传递基指针的原型函数，则可能会修复此警告。