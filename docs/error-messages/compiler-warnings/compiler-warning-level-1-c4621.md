---
title: 编译器警告（等级1） C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: 9dd4defe18a94f65e265d02f6c26c715667cd696
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052589"
---
# <a name="compiler-warning-level-1-c4621"></a>编译器警告（等级1） C4621

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