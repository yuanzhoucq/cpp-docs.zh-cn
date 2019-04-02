---
title: 编译器错误 C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781401"
---
# <a name="compiler-error-c3612"></a>编译器错误 C3612

type： 密封的类不能是抽象

通过使用定义的类型`value`密封的默认情况下，和一个类是抽象的除非它实现了其基类的所有方法。 密封的抽象类既不是一个基类，也可以将它实例化。

有关详细信息，请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```