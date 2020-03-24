---
title: 编译器警告（等级 1）C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: a48934fd097f9039988db32511ca87cbd66b22d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199742"
---
# <a name="compiler-warning-level-1-c4621"></a>编译器警告（等级 1）C4621

找不到类型 "type" 的 "operator--" 后缀形式，请使用前缀形式

没有为给定的类型定义后缀减量运算符。 编译器使用了重载的前缀运算符。

可以通过定义后缀 `--` 运算符来避免此警告。 创建 `--` 运算符的两参数版本，如下所示：

```cpp
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
