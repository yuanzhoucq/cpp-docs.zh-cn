---
title: 编译器错误 C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d35ded4b06423be53911f3efd0b55d75cb979773
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212808"
---
# <a name="compiler-error-c2248"></a>编译器错误 C2248

"*member*"：无法访问 "*class*" 类中声明的 "*access_level*" 成员

派生类的成员不能访问 **`private`** 基类的成员。 不能访问 **`private`** 或 **`protected`** 类实例的成员。

## <a name="example"></a>示例

下面的示例在从类外部访问类的私有或受保护成员时，生成 C2248。 若要解决此问题，请不要在类的外部直接访问这些成员。 使用公共成员数据和成员函数与类进行交互。

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

公开 C2248 的另一个一致性问题是使用模板好友和专用化。 若要解决此问题，请使用空模板参数列表 <> 或特定模板参数来声明友元模板函数。

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

公开 C2248 的另一个一致性问题是在您尝试声明一个类的友元，而当该类对类的作用域中的友元声明不可见时。 若要解决此问题，请向封闭类授予友元。

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```
