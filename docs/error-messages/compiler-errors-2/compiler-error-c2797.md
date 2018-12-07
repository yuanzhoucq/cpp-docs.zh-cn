---
title: 编译器错误 C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 04a7b2b1d33ab7efa77563406ab3c12831cf80fc
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518302"
---
# <a name="compiler-error-c2797"></a>编译器错误 C2797

（已过时）未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。

此警告是 Visual Studio 2015 中已过时。 在 Visual Studio 2013 和早期版本中，Visual c + + 编译器未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。 在 Visual Studio 2013 Update 3 之前，这已在无提示的情况下转换为函数调用，从而将导致代码生成错误。 Visual Studio 2013 Update 3 将其报告为错误。

此示例生成 C2797：

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

此示例也生成 C2797：

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

若要解决此问题，你可以使用内部列表的显式构造。 例如：

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

如果无需初始化列表：

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

（Visual Studio 2013 中的编译器会在 Visual Studio 2013 Update 3 之前隐式执行它。）