---
title: "值类和结构 (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- value struct
- value class
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3943b70d68eeeda91ddc6f8f1737e838d696e16
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="value-classes-and-structs-ccx"></a>值类和结构 (C++/CX)
A*值结构*或*值类*是一个 Windows 运行时兼容的 POD （"纯旧数据结构"）。 它具有固定大小且只包含字段；与 ref 类不同，它没有属性。  
  
 下面的示例演示如何声明和初始化值结构。  
  
```  
  
// in mainpage.xaml.h:  
    value struct TestStruct  
    {  
        Platform::String^ str;  
        int i;  
    };  
  
    value struct TestStruct2  
    {  
        TestStruct ts;  
        Platform::String^ str;  
        int i;  
    };  
  
// in mainpage.cpp:  
    // Initialize a value struct with an int and String  
    TestStruct ts = {"I am a TestStruct", 1};  
  
    // Initialize a value struct that contains  
    // another value struct, an int and a String  
    TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2};  
  
    // Initialize value struct members individually.  
    TestStruct ts3;   
    ts3.i = 108;  
    ts3.str = "Another way to init a value struct.";  
  
```  
  
 将一个值类型的变量分配给另一个变量时，该值被复制，因此，两个变量均有自己的数据副本。  值结构是一种具有固定大小的结构，它只包含公共数据字段并使用 `value struct` 关键字来声明。  
  
  值类则类似于 `value struct` ，只不过必须为其字段显式给定公共可访问性。 使用 `value class` 关键字来声明它。  
  
 值结构或值类只能作为字段基本数值类型、 枚举类、 包含`Platform::String^`，或[platform:: ibox \<T > ^](../cppcx/platform-ibox-interface.md)其中 T 是数值类型或枚举类或是值类或结构。 `IBox<T>^` 字段的值可以是 `nullptr`，这是 C++ 实现 “可以为 null 的值类型”概念的方式。  
  
 将 `Platform::String^` 或 `IBox<T>^` 类型作为成员包含在内的值类型或结构不支持 `memcpy`。  
  
 由于 `value class` 或 `value struct` 的所有成员都是公共成员并且将发送到元数据中，因此不允许标准 C++ 类型。 这与 ref 类不同，ref 类可包含 `private` 或 `internal` 标准 C++ 类型。  
  
 下面的代码片段声明 `Coordinates` 和 `City` 类型为值结构。 请注意，其中一个 `City` 数据成员是 `GeoCoordinates` 类型。 一个 `value struct` 可以包含其他值结构作为成员。  
  
 [!code-cpp[cx_classes#07](../cppcx/codesnippet/CPP/classesstructs/class1.h#07)]  
  
## <a name="parameter-passing-for-value-types"></a>值类型的参数传递  
 如果某个值类型用作函数或方法参数，则它通常通过值传递。 对于较大的对象，这会导致性能问题。 在 Visual Studio2013 和早期版本中，C++/CX 中的值类型始终通过值传递。 在 Visual Studio 2015 及更高版本中，可以通过引用或值来传递值类型。  
  
 若要声明通过值传递值类型的参数，请使用如下所示的代码：  
  
```  
void Method1(MyValueType obj);  
```  
  
 若要声明通过引用传递值类型参数，请使用引用符号 (&)，如下所示：  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Method2 中的类型是对 MyValueType 的引用，并且与标准 C++ 中引用类型的工作方式相同。  
  
 当从另一种语言（如 C# 中）调用 Method1 时，无需使用 `ref` 或 `out` 关键字。 调用 Method2 时，请使用 `ref` 关键字。  
  
```  
Method2(ref obj);  
```  
  
 也可以使用指针符号 (*) 来用引用方式传递值类型。 其他语言中与调用方有关的行为都是相同的（C# 中的调用方使用 `ref` 关键字），但在方法中，类型是指向值类型的指针。  
  
## <a name="nullable-value-types"></a>可以为 null 的值类型  
 如前所述，值类或值结构可以具有类型的字段[platform:: ibox\<T > ^](../cppcx/platform-ibox-interface.md)— 例如， `IBox<int>^`。 此类字段的值可以是对 `int` 类型有效的任何数值，也可以是 `nullptr`。 对于可以为 null 的字段，可将其作为实参传递给已将形参声明为可选参数的方法，或传递到值类型不必具有值的任何其他地方。  
  
 下面的示例演示如何初始化具有可以为 null 的字段的结构。  
  
```  
public value struct Student  
{  
    Platform::String^ Name;  
    int EnrollmentYear;  
    Platform::IBox<int>^ GraduationYear; // Null if not yet graduated.   
};  
//To create a Student struct, one must populate the nullable type.   
MainPage::MainPage()  
{  
    InitializeComponent();  
  
    Student A;  
    A.Name = "Alice";  
    A.EnrollmentYear = 2008;  
    A.GraduationYear = ref new Platform::Box<int>(2012);  
  
    Student B;  
    B.Name = "Bob";  
    B.EnrollmentYear = 2011;  
    B.GraduationYear = nullptr;  
  
    IsCurrentlyEnrolled(A);  
    IsCurrentlyEnrolled(B);  
}  
bool MainPage::IsCurrentlyEnrolled(Student s)  
{  
    if (s.GraduationYear == nullptr)  
    {  
        return true;  
    }  
    return false;  
}  
  
```  
  
 可通过相同的方式使值结构本身可以为 null，如此处所示：  
  
```  
  
public value struct MyStruct  
{  
public:  
    int i;  
    Platform::String^ s;  
};  
  
public ref class MyClass sealed  
{  
public:  
    property Platform::IBox<MyStruct>^ myNullableStruct;  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)   
 [Ref 类和结构 (C++/CX)](../cppcx/ref-classes-and-structs-c-cx.md)