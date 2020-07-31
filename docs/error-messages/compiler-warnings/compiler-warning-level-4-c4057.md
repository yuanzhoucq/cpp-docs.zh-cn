---
title: 编译器警告（等级 4）C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: d0bae91af3c2bfed97e252a74232e2a1bd778347
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225288"
---
# <a name="compiler-warning-level-4-c4057"></a>编译器警告（等级 4）C4057

“operator”: “identifier1”与“identifier2”在稍微不同的基类型间接寻址上不同

两个指针表达式引用不同的基类型。 使用表达式时无需转换。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 混合签名和未签名的类型。

1. 混合 **`short`** **`long`** 类型和类型。
