---
title: 编译器错误 C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6b15d867bbaf66f511cbda200d692f5db4371ab3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400157"
---
# <a name="compiler-error-c3771"></a>编译器错误 C3771

“标识符”: 在最近的命名空间范围内无法找到友元声明

无法在当前命名空间中找到指定模板的类模板声明 *标识符* 。

### <a name="to-correct-this-error"></a>更正此错误

- 确保在当前命名空间中定义了模板标识符的类模板声明，或模板标识符是完全限定的名称。

## <a name="example"></a>示例

下列代码示例在 `NA`命名空间中声明一个类模板和函数，但试图在 `NB`命名空间中声明友元函数模板。

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>请参阅

[模板](../../cpp/templates-cpp.md)