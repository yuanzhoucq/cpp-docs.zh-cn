---
title: 编译器警告（等级 1）C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574260"
---
# <a name="compiler-warning-level-1-c4612"></a>编译器警告（等级 1）C4612

> 包含文件名中有错误

## <a name="remarks"></a>备注

当文件名不正确或缺失时，此警告与 **#pragma include_alias** 一起出现。

参数 **#pragma include_alias**语句可以使用引号形式 ("*filename*") 或尖括号形式 (\<*filename*>)，但两者必须使用相同的形式。

## <a name="example"></a>示例

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```