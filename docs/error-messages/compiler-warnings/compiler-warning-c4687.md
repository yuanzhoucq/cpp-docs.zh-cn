---
title: 编译器警告 C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 50551faf817f83d8a4af848a75af67ebe7004fe7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635470"
---
# <a name="compiler-warning-c4687"></a>编译器警告 C4687

class： 密封的抽象类不能实现接口 interface

密封的抽象类型是通常仅用于包含静态成员函数。

有关详细信息，请参阅[抽象](../../windows/abstract-cpp-component-extensions.md)并[密封](../../windows/sealed-cpp-component-extensions.md)。

默认情况下，C4687 颁发为错误。 可以取消与 C4687[警告](../../preprocessor/warning.md)杂注。 如果不能确定你想要在密封的抽象类型中实现一个接口，则可以取消 C4687。

## <a name="example"></a>示例

下面的示例生成 C4687。

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```