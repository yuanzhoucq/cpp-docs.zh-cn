---
title: 编译器警告 （等级 1） C4621 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4621
dev_langs:
- C++
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70b9273e1c3a91db37be6bee2c1c33a0a4e30b17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090823"
---
# <a name="compiler-warning-level-1-c4621"></a>编译器警告（等级 1）C4621

任何后缀形式的 operator--找到类型 type，使用前缀形式

不没有为给定的类型定义任何后缀递减运算符。 编译器使用了重载的前缀运算符。

通过定义后缀可以避免此警告`--`运算符。 创建的两个参数版本`--`运算符，如下所示：

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