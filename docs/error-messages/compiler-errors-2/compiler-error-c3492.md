---
title: 编译器错误 C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: facd8c78e775945924d77b09f9dc754bdc301ddd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038814"
---
# <a name="compiler-error-c3492"></a>编译器错误 C3492

“var”: 不能捕获匿名联合的成员

不能捕获未命名联合的成员。

### <a name="to-correct-this-error"></a>更正此错误

- 为联合提供一个名称，并将整个此联合结构传递到 lambda 表达式的捕获列表。

## <a name="example"></a>示例

以下示例将生成 C3492，因为它捕获匿名联合的成员：

```
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

## <a name="example"></a>示例

通过给此联合提供名称以及将整个联合结构传递给 lambda 表达式的捕获列表，下面的示例解析了 C3492：

```
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)