---
title: "编译器支持类型特征（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__is_simple_value_class"
  - "__has_trivial_destructor"
  - "__has_assign"
  - "__is_union"
  - "__is_class"
  - "__is_abstract"
  - "__has_trivial_assign"
  - "__has_virtual_destructor"
  - "__is_ref_array"
  - "__is_base_of"
  - "__has_copy"
  - "__is_polymorphic"
  - "__has_nothrow_constructor"
  - "__is_ref_class"
  - "__is_delegate"
  - "__is_convertible_to"
  - "__is_value_class"
  - "__is_interface_class"
  - "__has_nothrow_copy"
  - "__is_sealed"
  - "__has_trivial_constructor"
  - "__has_trivial_copy"
  - "__is_enum"
  - "__has_nothrow_assign"
  - "__has_finalizer"
  - "__is_empty"
  - "__is_pod"
  - "__has_user_destructor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__is_class 关键字 [C++]"
  - "__is_pod 关键字 [C++]"
  - "__is_delegate 关键字 [C++]"
  - "__is_value_class 关键字 [C++]"
  - "__has_copy 关键字 [C++]"
  - "__has_nothrow_copy 关键字 [C++]"
  - "__is_interface_class 关键字 [C++]"
  - "__is_sealed 关键字 [C++]"
  - "__is_convertible_to 关键字 [C++]"
  - "__is_ref_class 关键字 [C++]"
  - "__has_trivial_copy 关键字 [C++]"
  - "__has_user_destructor 关键字 [C++]"
  - "__is_abstract 关键字 [C++]"
  - "__is_empty 关键字 [C++]"
  - "__has_trivial_assign 关键字 [C++]"
  - "__has_nothrow_constructor 关键字 [C++]"
  - "__is_ref_array 关键字 [C++]"
  - "__is_base_of 关键字 [C++]"
  - "__has_nothrow_assign 关键字 [C++]"
  - "__has_virtual_destructor 关键字 [C++]"
  - "__has_finalizer 关键字 [C++]"
  - "__is_union 关键字 [C++]"
  - "__has_assign 关键字 [C++]"
  - "__has_trivial_destructor 关键字 [C++]"
  - "__is_polymorphic 关键字 [C++]"
  - "__is_enum 关键字 [C++]"
  - "__is_simple_value_class 关键字 [C++]"
  - "__has_trivial_constructor 关键字 [C++]"
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编译器支持类型特征（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编译器支持 *键入特征*, ，这表明在编译时类型的各项特征。  
  
## <a name="all-runtimes"></a>所有运行时  
 **备注**  
  
 类型特征对编写库的编程人员尤其有用。  
  
 以下列表包含编译器支持类型特征。 如果未满足类型特征的名称所指定的条件，则所有类型特征将返回 `false`。  
  
 (在以下列表中，代码示例都将仅在写 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]。 但除非另外声明，否则相应的类型特征在 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] 中也受支持。 术语“平台类型”是指 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类型或公共语言运行时类型中任一个。）  
  
-   `__has_assign(` `type` `)`  
  
     如果该平台或本机类型具有复制赋值运算符，则返回 true。  
  
    ```  
  
    ref struct R {  
    void operator=(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_assign(R));  
    }  
  
    ```  
  
-   `__has_copy(` `type` `)`  
  
     如果该平台或本机类型具有复制构造函数，则返回 true。  
  
    ```  
  
    ref struct R {  
    R(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_copy(R));  
    }  
  
    ```  
  
-   `__has_finalizer(` `type` `)`  
  
     （在 [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] 中不受支持。）如果 CLR 类型有终结器，则返回 true。 请参阅 [析构函数和终结器中 Visual c + +](../misc/destructors-and-finalizers-in-visual-cpp.md) 有关详细信息。  
  
    ```  
  
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
  
-   `__has_nothrow_assign(` `type` `)`  
  
     如果复制赋值运算符具有空异常规范，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    void operator=(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_nothrow_constructor(` `type` `)`  
  
     如果默认构造函数具有空异常规范，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    S() throw() {}  
    };  
  
    int main() {  
    __has_nothrow_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_nothrow_copy(` `type` `)`  
  
     如果复制构造函数具有空异常规范，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    S(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_assign(` `type` `)`  
  
     如果类型具有一个普通的、由编译器生成的赋值运算符，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_constructor(` `type` `)`  
  
     如果类型具有一个普通的、由编译器生成的构造函数，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_copy(` `type` `)`  
  
     如果类型具有一个普通的、由编译器生成的复制构造函数，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_trivial_destructor(` `type` `)`  
  
     如果类型具有一个普通的、由编译器生成的析构函数，则返回 true。  
  
    ```  
  
    // has_trivial_destructor.cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_destructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__has_user_destructor(` `type` `)`  
  
     如果该平台或本机类型具有用户声明的析构函数，则返回 true。  
  
    ```  
  
    // has_user_destructor.cpp  
  
    using namespace System;  
    ref class R {  
    ~R() {}  
    };  
  
    int main() {  
    Console::WriteLine(__has_user_destructor(R));  
    }  
  
    ```  
  
-   `__has_virtual_destructor(` `type` `)`  
  
     如果类型具有虚拟的析构函数，则返回 true。  
  
     `__has_virtual_destructor` 也适用于平台类型，且平台类型中任何用户定义的析构函数都是虚拟的析构函数。  
  
    ```  
  
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
  
-   `__is_abstract(` `type` `)`  
  
     如果类型为抽象类型，则返回 true。 本机抽象类型的详细信息，请参阅 [抽象](../windows/abstract-cpp-component-extensions.md)。  
  
     `__is_abstract` 也适用于平台类型。 具有至少一个成员的接口为抽象类型，就像是具有至少一个抽象成员的引用类型。 有关抽象的平台类型的详细信息，请参阅 [抽象类](../cpp/abstract-classes-cpp.md)  
  
    ```  
  
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
  
-   `__is_base_of(` `base` `,` `derived` `)`  
  
     如果第一种类型是第二种类型的基类，或如果这两种类型相同，则返回 true。  
  
     `__is_base_of` 也适用于平台类型。 例如，它将返回 true，如果第一个类型为 [接口类](../windows/interface-class-cpp-component-extensions.md) 和第二个类型实现的接口。  
  
    ```  
  
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
  
-   `__is_class(` `type` `)`  
  
     如果类型为本机类或结构，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_class(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_convertible_to(` `from` `,`  `to` `)`  
  
     如果第一种类型可被转换为第二种类型，则返回 true。  
  
    ```  
  
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
  
-   `__is_delegate(` `type` `)`  
  
     如果 `type` 是一个委托，则返回 true。 有关详细信息，请参阅 [委托 （c + + 组件扩展）](../windows/delegate-cpp-component-extensions.md)。  
  
    ```  
  
    delegate void MyDel();  
    int main() {  
    System::Console::WriteLine(__is_delegate(MyDel));  
    }  
  
    ```  
  
-   `__is_empty(` `type` `)`  
  
     如果类型没有实例数据成员，则返回 true。  
  
    ```  
  
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
  
-   `__is_enum(` `type` `)`  
  
     如果类型为本机枚举，则返回 true。  
  
    ```  
  
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
  
-   `__is_interface_class(` `type` `)`  
  
     如果已传递一个平台接口，则返回 true。 有关详细信息，请参阅 [接口类](../windows/interface-class-cpp-component-extensions.md)。  
  
    ```  
  
    // is_interface_class.cpp  
  
    using namespace System;  
    interface class I {};  
    int main() {  
    Console::WriteLine(__is_interface_class(I));  
    }  
  
    ```  
  
-   `__is_pod(` `type` `)`  
  
     如果类型为没有构造函数、或私有或受保护的非静态成员、没有基类以及没有虚函数的类或联合，则返回 true。 请参见 C++ 标准，8.5.1/1、9/4 和 3.9/10 小节以获取有关 POD 的详细信息。  
  
     `__is_pod` 将在基本类型上返回 false。  
  
    ```  
  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_pod(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_polymorphic(` `type` `)`  
  
     如果本机类型具有虚函数，则返回 true。  
  
    ```  
  
    #include <stdio.h>  
    struct S {  
    virtual void Test(){}  
    };  
  
    int main() {  
    __is_polymorphic(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
  
    ```  
  
-   `__is_ref_array(` `type` `)`  
  
     如果已传递一个平台数组，则返回 true。 有关详细信息，请参阅 [数组](../windows/arrays-cpp-component-extensions.md)。  
  
    ```  
  
    using namespace System;  
    int main() {  
    array<int>^ x = gcnew array<int>(10);  
    Console::WriteLine(__is_ref_array(array<int>));  
    }  
  
    ```  
  
-   `__is_ref_class(` `type` `)`  
  
     如果已传递一个引用类，则返回 true。 用户定义的引用类型的详细信息，请参阅 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
    ```  
  
    using namespace System;  
    ref class R {};  
    int main() {  
    Console::WriteLine(__is_ref_class(Buffer));  
    Console::WriteLine(__is_ref_class(R));  
    }  
  
    ```  
  
-   `__is_sealed(` `type` `)`  
  
     如果已传递一个标记为密封的平台或本机类型，则返回 true。 有关详细信息，请参阅 [密封](../windows/sealed-cpp-component-extensions.md)。  
  
    ```  
  
    ref class R sealed{};  
    int main() {  
    System::Console::WriteLine(__is_sealed(R));  
    }  
  
    ```  
  
-   `__is_simple_value_class(` `type` `)`  
  
     如果已传递一个不包含对垃圾回收堆的引用的值类型，则返回 true。 用户定义的值类型的详细信息，请参阅 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
    ```  
  
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
  
-   `__is_union(` `type` `)`  
  
     如果类型是联合，则返回 true。  
  
    ```  
  
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
  
-   `__is_value_class(` `type` `)`  
  
     如果已传递一个值类型，则返回 true。 用户定义的值类型的详细信息，请参阅 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)。  
  
    ```  
  
    value struct V {};  
  
    int main() {  
    System::Console::WriteLine(__is_value_class(V));  
    }  
  
    ```  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
  `__has_finalizer(`*类型*`)` 不支持类型特征，因为此平台不支持终结器。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示如何使用类模板来公开的编译器类型特性 **/clr** 编译。 有关详细信息，请参阅 [Windows 运行时和托管模板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。  
  
```  
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
  
 **输出**  
  
```Output  
R is a ref class  
```  
  
## <a name="see-also"></a>另请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)