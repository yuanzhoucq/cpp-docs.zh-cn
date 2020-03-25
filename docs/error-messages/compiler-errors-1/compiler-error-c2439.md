---
title: 编译器错误 C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205356"
---
# <a name="compiler-error-c2439"></a>编译器错误 C2439

"identifier"：未能初始化成员

无法初始化类、结构或联合成员。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 尝试初始化间接基类或结构。

1. 尝试初始化类或结构的继承成员。 必须通过类或结构的构造函数来初始化继承的成员。
