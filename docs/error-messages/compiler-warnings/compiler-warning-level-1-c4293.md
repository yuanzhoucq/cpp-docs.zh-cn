---
title: 编译器警告（等级 1）C4293
description: 介绍 MSVC 编译器警告 C4293 的原因，并演示如何修复此警告。
ms.date: 07/15/2020
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 3b5a05d4a744b084f1cc34210a5374962064e85d
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446471"
---
# <a name="compiler-warning-level-1-c4293"></a>编译器警告（等级 1）C4293

> "*operator*"：移位计数为负或过大，未定义行为

如果移位计数为负或过大，则生成的映像的行为是不确定的。

## <a name="remarks"></a>备注

若要解决此问题，可以对第一个操作数使用强制转换，以将其扩展到结果类型的大小。

## <a name="example"></a>示例

下面的示例生成 C4293，并显示修复方法的方法：

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi)
{
   return (hi << 32) | lo;   // C4293

   // In C, try the following line instead:
   // return ( (unsigned __int64)hi << 32) | lo;
   // In C++, try this line instead:
   // return (static_cast<unsigned __int64>(hi) << 32) | lo;
}
```
