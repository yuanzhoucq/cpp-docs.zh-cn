---
title: 编译器错误 C2439 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419bf7be45a1383135d0231cd059837e1fe62729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058403"
---
# <a name="compiler-error-c2439"></a>编译器错误 C2439

identifier： 无法初始化成员

无法初始化类、 结构或联合成员。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 尝试初始化间接基类或结构。

1. 尝试初始化的类或结构继承的成员。 必须由类或结构的构造函数初始化继承的成员。