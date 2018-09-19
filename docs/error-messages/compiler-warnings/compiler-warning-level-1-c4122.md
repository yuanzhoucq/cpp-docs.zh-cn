---
title: 编译器警告 （等级 1） C4122 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4122
dev_langs:
- C++
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37f7928b1aa89eb66da95b4383084b2011387e0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075406"
---
# <a name="compiler-warning-level-1-c4122"></a>编译器警告（等级 1）C4122

“function”: alloc_text 仅适用于带 C 链接的函数

**alloc_text** 杂注仅适用于使用 **extern c**声明的函数。 它不能与外部 C++ 函数一起使用。

将忽略杂注。