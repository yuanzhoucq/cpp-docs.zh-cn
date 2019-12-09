---
title: 编译器错误 C2521
ms.date: 11/04/2016
f1_keywords:
- C2521
helpviewer_keywords:
- C2521
ms.assetid: 6042821b-e345-4a54-a7e9-a2c9019ea016
ms.openlocfilehash: cabd13b3292995d2baa8c5c66e9bc9ee85118c44
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746443"
---
# <a name="compiler-error-c2521"></a>编译器错误 C2521

函数不采用任何自变量

尝试对析构函数或终结器使用参数。

有关详细信息，请参阅[析构函数和终结](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)器。

## <a name="example"></a>示例

下面的示例生成 C2521。

```cpp
// C2521.cpp
// compile with: /clr
ref class R {
protected:
   !R() {}

public:
   void CleanUp() {
      this->!R(4);   // C2521
      this->!R();   // OK
   }
};

int main() {
   R^ r = gcnew R();
   r->CleanUp();
}
```
