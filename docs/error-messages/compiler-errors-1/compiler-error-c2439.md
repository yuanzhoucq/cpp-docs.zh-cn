---
title: 编译器错误 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: f71112d3f37f3e4d1a4f41bade95726d7aa0a0bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644348"
---
# <a name="compiler-error-c2439"></a>编译器错误 C2439

identifier： 无法初始化成员

无法初始化类、 结构或联合成员。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 尝试初始化间接基类或结构。

1. 尝试初始化的类或结构继承的成员。 必须由类或结构的构造函数初始化继承的成员。