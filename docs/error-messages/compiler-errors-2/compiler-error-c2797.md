---
title: 编译器错误 C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: ccd007bf193bd6529748004a96745fafcb9f3226
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447826"
---
# <a name="compiler-error-c2797"></a>编译器错误 C2797

（已过时）未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。

此警告是 Visual Studio 2015 中已过时。 在 Visual Studio 2013 和早期版本中，MicrosoftC++编译器未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。 在 Visual Studio 2013 Update 3 之前，这已在无提示的情况下转换为函数调用，从而将导致代码生成错误。 Visual Studio 2013 Update 3 将其报告为错误。

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