---
title: 编译器错误 C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: ea7341b9c587a764c7366fa7b7c89e4fc67bc7d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230852"
---
# <a name="compiler-error-c3490"></a>编译器错误 C3490

无法修改 var，因为正在通过 const 对象对其进行访问

在方法中声明的 lambda 表达式 **`const`** 不能修改不可变成员数据。

### <a name="to-correct-this-error"></a>更正此错误

- **`const`** 从方法声明删除修饰符。

## <a name="example"></a>示例

下面的示例生成 C3490，因为它修改方法中的成员变量 `_i` **`const`** ：

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>示例

下面的示例通过 **`const`** 从方法声明中移除修饰符来解析 C3490：

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
