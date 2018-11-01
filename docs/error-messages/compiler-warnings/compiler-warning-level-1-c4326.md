---
title: 编译器警告（等级 1）C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d14a1902db4dcf2224ce6a58db120a81ebb5620f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601157"
---
# <a name="compiler-warning-level-1-c4326"></a>编译器警告（等级 1）C4326

> 返回类型*函数*'应是'*type1*而不是 of*type2*

## <a name="remarks"></a>备注

一个函数返回的类型不是*type1*。 例如，使用[/Za](../../build/reference/za-ze-disable-language-extensions.md)，**主要**未返回**int**。

## <a name="example"></a>示例

下面的示例生成 C4326 并演示如何修复此错误：

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```