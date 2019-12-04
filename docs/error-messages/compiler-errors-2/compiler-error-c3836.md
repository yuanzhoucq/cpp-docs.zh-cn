---
title: 编译器错误 C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741399"
---
# <a name="compiler-error-c3836"></a>编译器错误 C3836

静态构造函数不允许有成员初始值设定项列表

托管类不能具有同样具有成员初始化列表的静态构造函数。 静态类构造函数由公共语言运行时调用，用于执行类初始化，初始化静态数据成员。

## <a name="example"></a>示例

下面的示例生成 C3836：

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
