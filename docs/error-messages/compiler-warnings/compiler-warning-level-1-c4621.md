---
title: 编译器警告（等级 1）C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: d35c4143d5b90c7a6a49337931dad4ba73804f20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555619"
---
# <a name="compiler-warning-level-1-c4621"></a>编译器警告（等级 1）C4621

任何后缀形式的 operator--找到类型 type，使用前缀形式

不没有为给定的类型定义任何后缀递减运算符。 编译器使用了重载的前缀运算符。

可以通过定义后缀 `--` 运算符来避免此警告。 创建的两个参数版本`--`运算符，如下所示：

```
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
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
   --a;
   a--;   // C4621
}
```