---
title: 编译器警告（等级 1）C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531010"
---
# <a name="compiler-warning-level-1-c4377"></a>编译器警告（等级 1）C4377

本机类型是私有默认设置。-d1PrivateNativeTypes 已被否决

在早期版本中，在程序集的本机类型是公共的默认值，并且将内部、 未记录的编译器选项 (**/d1PrivateNativeTypes**) 可将其变为专用。

所有类型，本机和 CLR，现在是私有程序集，默认情况下使 **/d1PrivateNativeTypes**不再需要。

## <a name="example"></a>示例

下面的示例生成 C4377。

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```