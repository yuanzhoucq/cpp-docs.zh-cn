---
title: 编译器错误 C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 337cd7f37bf94c7a3d5cffe6b167d4661e3b0a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751451"
---
# <a name="compiler-error-c3084"></a>编译器错误 C3084

“函数”: 终结器/析构函数不能是“关键字”

未正确声明终结器或析构函数。

例如，析构函数不应标记为密封。  派生类型无法访问析构函数。  有关详细信息，请参阅[如何：定义和使用类和结构（C++/cli）中](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)的[显式重写](../../extensions/explicit-overrides-cpp-component-extensions.md)和析构函数和终结器。

## <a name="example"></a>示例

以下示例生成 C3084。

```cpp
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```
