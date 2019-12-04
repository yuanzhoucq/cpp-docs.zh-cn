---
title: 编译器错误 C2552
ms.date: 11/04/2016
f1_keywords:
- C2552
helpviewer_keywords:
- C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
ms.openlocfilehash: 7f3e4cfc46655c5201e7a79a9333f532a8fcab9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740801"
---
# <a name="compiler-error-c2552"></a>编译器错误 C2552

“标识符”：不能用初始值设定项列表初始化非聚合

错误初始化了聚合标识符。

[聚合](../../c-language/initializing-aggregate-types.md)定义为：

- 阵列

- 不具有以下项的类、结构和联合：

   - 构造函数

   - 私有成员或受保护成员

   - 基类

   - 虚函数

此外，Visual C++ 不允许在包含构造函数的聚合中使用数据类型。

以下内容表示在尝试对类型进行聚合初始化时可能触发 C2552 的原因：

- 类型拥有一个或多个用户定义的构造函数。

- 类型拥有一个或多个非静态的私有数据成员。

- 类型拥有一个或多个虚函数。

- 类型拥有一个基类。

- 类型是 ref 类或 CLR 接口。

- 类型拥有一个其元素具有析构函数的不固定的维度数组（零数组）。

以下示例生成 C2552：

```cpp
// C2552.cpp
// compile with: /clr
#include <string>
using namespace std;

struct Pair_Incorrect {
private:
   string m_name;
   double m_val;
};

struct Pair_Correct1 {
public:
   Pair_Correct1(string name, double val)
      : m_name(name), m_val(val) {}

private:
   string m_name;
   double m_val;
};

struct Pair_Correct2 {
public:
   string m_name;
   double m_val;
};

int main() {
   // To fix, add a constructor to this class and use it for
   // initializing the data members, see Pair_Correct1 (below)
   // or
   // Do not have any private or protected non-static data members,
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in
   // case your object model requires some non-static data members to
   // be private or protected

   string name("John");
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552

   // initialize a CLR immutable value type that has a constructor
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552

   Pair_Correct1 pair2( name, 0.0 );
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );
   Pair_Correct2 pair4 = { name, 0.0 };
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);
}
```
