---
title: 编译器错误 C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 01e229fe0ae5bf9e04c577bb653ff1ed7fdb33bf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773891"
---
# <a name="compiler-error-c3084"></a>编译器错误 C3084

“函数”: 终结器/析构函数不能是“关键字”

未正确声明终结器或析构函数。

例如，析构函数不应标记为密封。  派生类型无法访问析构函数。  有关详细信息，请参阅[显式重写](../../extensions/explicit-overrides-cpp-component-extensions.md)和[析构函数和终结器中如何：定义和使用类和结构 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

## <a name="example"></a>示例

以下示例生成 C3084。

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```