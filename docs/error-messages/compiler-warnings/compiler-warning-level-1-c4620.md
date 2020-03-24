---
title: 编译器警告（等级 1）C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: f044d3e10928bc1aaa1e111d01d04b8562b5c025
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185888"
---
# <a name="compiler-warning-level-1-c4620"></a>编译器警告（等级 1）C4620

未找到类型“type”的“运算符 ++”后缀形式，请使用前缀形式

没有为给定的类型定义后缀递增运算符。 编译器使用了重载的前缀运算符。

可以通过定义后缀 `++` 运算符来避免此警告。 创建的 `++` 运算符的两个参数版本如下所示：

```cpp
// C4620.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator++()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator++(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   ++a;
   a++;   // C4620
}
```
