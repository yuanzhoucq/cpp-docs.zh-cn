---
title: 编译器警告 C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631609"
---
# <a name="compiler-warning-c4687"></a>编译器警告 C4687

> "*class*": 密封的抽象类不能实现接口 "*interface*"

## <a name="remarks"></a>备注

密封的抽象类型通常仅用于保存静态成员函数。

有关详细信息, 请参阅[abstract](../../extensions/abstract-cpp-component-extensions.md)和[sealed](../../extensions/sealed-cpp-component-extensions.md)。

默认情况下, C4687 作为错误发出。 可以通过[警告](../../preprocessor/warning.md)杂注取消 C4687。 如果确定要在密封的抽象类型中实现接口, 可以取消 C4687。

## <a name="example"></a>示例

下面的示例生成 C4687。

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
