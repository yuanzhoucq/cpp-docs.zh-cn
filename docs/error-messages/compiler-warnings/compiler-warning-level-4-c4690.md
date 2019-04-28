---
title: 编译器警告（等级 4）C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324579"
---
# <a name="compiler-warning-level-4-c4690"></a>编译器警告（等级 4）C4690

> \[ emitidl (pop)]: 比入栈的多个

## <a name="remarks"></a>备注

[emitidl](../../windows/emitidl.md) 特性的出栈次数比入栈次数多一次。

## <a name="example"></a>示例

下面的示例生成 C4690。 若要解决此问题，请确保该属性将弹出推送的次数完全相同。

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
