---
title: 编译器错误 C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645934"
---
# <a name="compiler-error-c3420"></a>编译器错误 C3420

“finalizer”: 终结器不能为虚

终结器只能从其封闭类型进行非虚拟调用。 因此，声明虚拟终结器是错误的。

有关详细信息，请参阅[析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>示例

下面的示例生成 C3420。

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```