---
title: 编译器警告（等级 1）C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: e882cabdf38fd9bc926fbaa04352ba9d0ace90ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174409"
---
# <a name="compiler-warning-level-1-c4965"></a>编译器警告（等级 1）C4965

整数0的隐式框;使用 nullptr 或显式强制转换

可视C++功能值类型的隐式装箱。 使用托管扩展导致空赋值的指令C++现在变为对装箱的 int 的赋值。

有关更多信息，请参见 [装箱](../../extensions/boxing-cpp-component-extensions.md)中定义的接口的私有 C++ 特定实现。

## <a name="example"></a>示例

下面的示例生成 C4965。

```cpp
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
