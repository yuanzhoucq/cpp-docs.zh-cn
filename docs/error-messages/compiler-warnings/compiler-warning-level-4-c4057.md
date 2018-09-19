---
title: 编译器警告 （等级 C4057 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b10ce6b67fd24b4b8db01177af0225deab9dba4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088002"
---
# <a name="compiler-warning-level-4-c4057"></a>编译器警告（等级 4）C4057

“operator”: “identifier1”与“identifier2”在稍微不同的基类型间接寻址上不同

两个指针表达式引用不同的基类型。 使用表达式时无需转换。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 混合签名和未签名的类型。

1. 混合 **short** 和 **long** 类型。