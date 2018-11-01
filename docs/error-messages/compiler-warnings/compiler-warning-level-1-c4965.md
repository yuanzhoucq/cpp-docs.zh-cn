---
title: 编译器警告（等级 1）C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 7d77df395d680b467d1a04a3f59c9822842f99f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653097"
---
# <a name="compiler-warning-level-1-c4965"></a>编译器警告（等级 1）C4965

整数 0; 的隐式装箱请使用 nullptr 或显式强制转换

Visual c + + 功能值类型隐式的装箱。 现在使用的 c + + 托管扩展分配空值会导致指令将成为赋值为装箱的整数。

有关更多信息，请参见 [装箱](../../windows/boxing-cpp-component-extensions.md)中定义的接口的私有 C++ 特定实现。

## <a name="example"></a>示例

下面的示例生成 C4965。

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```