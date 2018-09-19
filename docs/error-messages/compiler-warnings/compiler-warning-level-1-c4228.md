---
title: 编译器警告 （等级 1） C4228 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4228
dev_langs:
- C++
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab568ef6622bfa10f0e10566ec92dfaee71d22c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047949"
---
# <a name="compiler-warning-level-1-c4228"></a>编译器警告（等级 1）C4228

使用了非标准扩展： 忽略声明符列表中逗号后面的限定符

喜欢使用的限定符**const**或`volatile`逗号声明变量时是 Microsoft 扩展后 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>示例

```
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```