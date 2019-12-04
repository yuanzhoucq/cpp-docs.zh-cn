---
title: 编译器错误 C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: 5f44c94cbb3c945406835816d8fc6ed7c39480eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742621"
---
# <a name="compiler-error-c3633"></a>编译器错误 C3633

不能将 "member" 定义为托管 "type" 的成员

CLR 引用类数据成员不能为非 POD C++类型。  只能在 CLR 类型中实例化 POD 本机类型。  例如，POD 类型不能包含复制构造函数或赋值运算符。

## <a name="example"></a>示例

下面的示例生成 C3633。

```cpp
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
