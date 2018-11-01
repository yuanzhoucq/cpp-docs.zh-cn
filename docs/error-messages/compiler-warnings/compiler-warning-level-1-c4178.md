---
title: 编译器警告（等级 1）C4178
ms.date: 11/04/2016
f1_keywords:
- C4178
helpviewer_keywords:
- C4178
ms.assetid: 2c2c8f97-a5c4-47cd-8dd2-beea172613f3
ms.openlocfilehash: 76e2b0e6ee42e8f32eb462336721d860cff006a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540083"
---
# <a name="compiler-warning-level-1-c4178"></a>编译器警告（等级 1）C4178

对于 switch 表达式的类型而言，case 常量“constant”过大

`switch` 表达式中的 case 常量不符合向其分配的类型。

## <a name="example"></a>示例

```
// C4178.cpp
// compile with: /W1
int main()
{
    int i;  // maximum size of unsigned long int is 4294967295
    switch( i )
    {
        case 4294967295:   // OK
            break;
        case 4294967296:   // C4178
            break;
    }
}
```