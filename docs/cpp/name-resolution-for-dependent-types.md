---
title: 依赖类型的名称解析
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: de40bd056fe351e679ff32d9908c068ea4c6752a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227304"
---
# <a name="name-resolution-for-dependent-types"></a>依赖类型的名称解析

**`typename`** 在模板定义中使用限定名，告诉编译器给定的限定名称标识类型。 有关详细信息，请参阅[类型名称](../cpp/typename.md)。

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

相关名称的名称查找从模板定义的上下文中检查名称-在下面的示例中，此上下文会发现 `myFunction(char)` 和模板实例化的上下文。在下面的示例中，模板在 main 中实例化;因此，在 `MyNamespace::myFunction` 实例化点可见，并将其选取为更好的匹配项。 如果重命名 `MyNamespace::myFunction`，则将调用 `myFunction(char)`。

所有名称都会得到解析，就如同它们是依赖名称一样。 尽管如此，如果存在任何可能的冲突，建议您使用完全限定名。

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>输出

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>模板消除歧义

Visual Studio 2012 强制执行 c + + 98/03/11 标准规则，消除了 "template" 关键字的歧义。 在下面的示例中，Visual Studio 2010 将接受不符合要求的行和一致的行。  Visual Studio 2012 只接受符合要求的行。

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

需要符合消除歧义规则，因为默认情况下，C++ 假定 `AY::Rebind` 不是模板，因此编译器会将后面的“`<`”解释为小于。 它必须知道 `Rebind` 是模板，这样才能正确地将“`<`”分析为尖括号。

## <a name="see-also"></a>另请参阅

[名称解析](../cpp/templates-and-name-resolution.md)
