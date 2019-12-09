---
title: 编译器错误 C3848
ms.date: 11/04/2016
f1_keywords:
- C3848
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
ms.openlocfilehash: 51a5cf6d866a5e5ee914a3d70365761749f79eea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761941"
---
# <a name="compiler-error-c3848"></a>编译器错误 C3848

类型为 "type" 的表达式会丢失一些常量可变限定符，以便调用 "function"

具有指定 const volatile 类型的变量只能调用使用相同或更大的 const volatile 限定定义的成员函数。

以下示例生成 C3848：

```cpp
// C3848.cpp
void glbFunc1()
{
}

typedef void (* pFunc1)();

struct S3
{
   operator pFunc1() // const
   {
      return &glbFunc1;
   }
};

int main()
{
   const S3 s3;
   s3();   // C3848, uncomment const qualifier
}
```
