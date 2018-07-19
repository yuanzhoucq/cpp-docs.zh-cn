---
title: 编译器警告 （等级 C4690 |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853317"
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
