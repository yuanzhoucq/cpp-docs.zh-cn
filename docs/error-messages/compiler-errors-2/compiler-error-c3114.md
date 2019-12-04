---
title: 编译器错误 C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6f548c72a0e95c533ed711fe9f2583a7abd6c500
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760756"
---
# <a name="compiler-error-c3114"></a>编译器错误 C3114

"argument"：不是有效的命名特性参数

为了使特性类的数据成员是有效的命名参数，不能将其标记 `static`、`const`或 `literal`。 如果属性为，则属性不得 `static` 并且必须具有 get 和 set 访问器。

有关详细信息，请参阅[属性](../../extensions/property-cpp-component-extensions.md)和[用户定义的属性](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3114。

```cpp
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```
