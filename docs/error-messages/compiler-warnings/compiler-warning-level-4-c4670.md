---
title: 编译器警告（等级 4）C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 15f0b249d9e91c0ebcc5655b5edffbd2d8cafa93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230605"
---
# <a name="compiler-warning-level-4-c4670"></a>编译器警告（等级 4）C4670

“identifier”：该基类不可访问

要在块中引发的对象的指定基类 **`try`** 不可访问。 不能实例化引发的对象。 检查基类继承了正确的访问说明符。

下面的示例生成 C4670：

```cpp
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```
