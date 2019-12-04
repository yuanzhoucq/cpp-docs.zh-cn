---
title: 编译器错误 C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: 61ff2c7f7e99698ffbd521153663b1ab27bd6fde
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741594"
---
# <a name="compiler-error-c3831"></a>编译器错误 C3831

"member"： "class" 不能有钉住的数据成员或返回钉住指针的成员函数

[pin_ptr （C++/cli）](../../extensions/pin-ptr-cpp-cli.md)的使用不正确。

## <a name="example"></a>示例

下面的示例生成 C3831：

```cpp
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
