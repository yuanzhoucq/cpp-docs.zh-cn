---
title: 编译器错误 C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: c2e92fec7c3faeda80bf7f0be3caa33e5d78295b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550275"
---
# <a name="compiler-error-c3669"></a>编译器错误 C3669

member： 重写的说明符 override 不允许在静态成员函数或构造函数

重写未正确指定。 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3669。

```
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```