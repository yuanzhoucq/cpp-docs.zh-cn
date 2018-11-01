---
title: 编译器支持类型特征 (C + + /cli 和 C + + /cli CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
ms.openlocfilehash: 5cd4d7feef01d1b7bedd407357c618ba208d06f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536183"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>编译器支持类型特征 (C + + /cli 和 C + + /cli CX)

Microsoft c + + 编译器支持*类型特征*C + /cli 和 C + + /CX 扩展，指示在编译时类型的各种特征。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

类型特征对编写库的编程人员尤其有用。

以下列表包含编译器支持类型特征。 所有类型特征将返回**false**如果不满足类型特征的名称指定的条件。

(在以下列表中，编写代码示例仅在 C + + /cli CLI。 但相应的类型特征也支持在 C + + /cli CX 除非另有说明。 "术语平台类型"是指 Windows 运行时类型或公共语言运行时类型。）

- `__has_assign(` *类型* `)`

   返回 **，则返回 true**如果平台或本机类型具有复制赋值运算符。

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *类型* `)`

   返回 **，则返回 true**如果平台或本机类型具有复制构造函数。

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *类型* `)`

   (不支持在 C + + /cli CX。)返回 **，则返回 true**如果 CLR 类型有终结器。 请参阅[析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)有关详细信息。

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(` *类型* `)`

   返回 **，则返回 true**如果复制赋值运算符具有空异常规范。

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(` *类型* `)`

   返回 **，则返回 true**如果默认构造函数具有空异常规范。

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(` *类型* `)`

   返回 **，则返回 true**如果复制构造函数具有空异常规范。

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(` *类型* `)`

   返回 **，则返回 true**如果该类型具有一个普通的、 由编译器生成的赋值运算符。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *类型* `)`

   返回 **，则返回 true**类型是否包含普通的、 由编译器生成的构造函数。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *类型* `)`

   返回 **，则返回 true**如果该类型具有一个普通的、 由编译器生成复制构造函数。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *类型* `)`

   返回 **，则返回 true**如果该类型具有一个普通的、 由编译器生成的析构函数。

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *类型* `)`

   返回 **，则返回 true**如果平台或本机类型具有用户声明析构函数。

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(` *类型* `)`

   返回 **，则返回 true**如果该类型具有虚拟析构函数。

   `__has_virtual_destructor` 也适用于平台类型，且平台类型中任何用户定义的析构函数都是虚拟的析构函数。

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(` *类型* `)`

   返回 **，则返回 true**类型是否为抽象类型。 有关本机抽象类型的详细信息，请参阅[抽象类](../cpp/abstract-classes-cpp.md)。

   `__is_abstract` 也适用于平台类型。 具有至少一个成员的接口为抽象类型，就像是具有至少一个抽象成员的引用类型。 有关抽象平台类型的详细信息，请参阅[抽象](../windows/abstract-cpp-component-extensions.md)。

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   返回 **，则返回 true**如果第一个类型为第二种类型的基类，如果这两种类型的相同。

   `__is_base_of` 也适用于平台类型。 例如，它将返回 **，则返回 true**如果第一个类型为[接口类](../windows/interface-class-cpp-component-extensions.md)和第二个类型实现接口。

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(` *类型* `)`

   返回 **，则返回 true**如果类型为本机类或结构。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   返回 **，则返回 true**如果第一个类型可以转换为第二个类型。

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(` *类型* `)`

   返回 **，则返回 true**如果`type`是一个委托。 有关详细信息，请参阅[委托 (C + + /cli 和 C + + /cli CX)](../windows/delegate-cpp-component-extensions.md)。

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *类型* `)`

   返回 **，则返回 true**如果类型没有实例数据成员。

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(` *类型* `)`

   返回 **，则返回 true**类型是否为本机枚举。

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(` *类型* `)`

   返回 **，则返回 true**如果传递一个平台接口。 有关详细信息，请参阅[接口类](../windows/interface-class-cpp-component-extensions.md)。

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *类型* `)`

   返回 **，则返回 true**如果类型是一个类或联合没有构造函数或私有或受保护的非静态成员、 基类和没有虚函数。 请参见 C++ 标准，8.5.1/1、9/4 和 3.9/10 小节以获取有关 POD 的详细信息。

   `__is_pod` 将在基本类型上返回 false。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *类型* `)`

   返回 **，则返回 true**如果本机类型具有虚函数。

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(` *类型* `)`

   返回 **，则返回 true**如果传递一个平台数组。 有关详细信息，请参阅[数组](../windows/arrays-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *类型* `)`

   返回 **，则返回 true**如果传递一个引用类。 用户定义的引用类型的详细信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *类型* `)`

   返回 **，则返回 true**如果传递一个平台或本机类型标记为密封。 有关详细信息，请参阅[密封](../windows/sealed-cpp-component-extensions.md)。

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *类型* `)`

   返回 **，则返回 true**如果传递不包含对垃圾回收堆引用的值类型。 用户定义的值类型的详细信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(` *类型* `)`

   返回 **，则返回 true**类型是否为联合。

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(` *类型* `)`

   返回 **，则返回 true**如果传递值类型。 用户定义的值类型的详细信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

`__has_finalizer(`*类型*`)`不支持类型特征，因为此平台不支持终结器。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

（此功能没有特定于平台的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

**示例**

下面的代码示例演示如何使用类模板来公开适用于 `/clr` 编译的编译器类型特征。 有关详细信息，请参阅[Windows 运行时和托管模板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](../windows/component-extensions-for-runtime-platforms.md)