---
title: 编译器错误 C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 481e0ac5a395b38bc9d1874959b010ecd71f9fb5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233374"
---
# <a name="compiler-error-c3114"></a>编译器错误 C3114

"argument"：不是有效的命名特性参数

为了使特性类的数据成员是有效的命名参数，不能将其标记为 **`static`** 、 **`const`** 或 **`literal`** 。 如果属性为，则属性不得为 **`static`** ，并且必须具有 get 和 set 访问器。

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
