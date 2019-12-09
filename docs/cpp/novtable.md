---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: a147af8f536923082df3a2d6d332150a57d6af1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857380"
---
# <a name="novtable"></a>novtable

**Microsoft 专用**

这是一个 **__declspec**扩展的属性。

这种形式的 **__declspec**可应用于任何类声明，但仅应用于纯接口类，即永远不会自行实例化的类。 **__Declspec**停止编译器生成代码以初始化类的构造函数和析构函数中的 vfptr。 在许多情况下，这将移除对与类关联的 vtable 的唯一引用，因此链接器将移除它。 使用这种形式的 **__declspec**可能导致代码大小大幅降低。

如果尝试实例化标记为**novtable**的类，然后访问类成员，则会收到访问冲突（AV）。

## <a name="example"></a>示例

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)