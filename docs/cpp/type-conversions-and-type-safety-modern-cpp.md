---
title: "类型转换和类型安全（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 类型转换和类型安全（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档标示符列出了常见类型转换问题，并描述如何在 C\+\+ 代码中避免它们。  
  
 当您编写C\+\+程序时，务必确保它是类型安全的。  这意味着每个变量、函数参数和函数返回值存储一种可接受的数据类型，涉及不同“有意义”类型的操作数，且不导致数据丢失、不正确的位组合解释或内存损坏。  程序的类型安全的定义是从不显式或隐式的把一种类型转换成另一种类型。  但是，有时需要类型转换，即使是不安全的转换。  例如，在变量类型 `int` 中,您可能需要存储浮点操作的结果，或者你可能需要项参数为有符号 `int` 值的函数传递一个无符号 `int` 值。  两个示例例举了不安全的数据转换,原因是它们可能会导致值的数据丢失或重新定义值。  
  
 当编译器检测到不安全的转换时，将发出错误或警告。  错误使得编译停止；警告允许继续编译，但在代码中会指示出一个可能的错误。  但是，即使您的程序编译后无警告，你的代码中仍然可能包含会导致错误结果的隐式类型转换。  在代码中，类型错误也能由显式转换或强制转换引入。  
  
## 隐式类型转换  
 当一个表达式包含不同的内置类型的操作数，且不存在显式转换，编译器会使用内置的*标准转换*来转换一个操作数，使得操作数类型相匹配。  编译器会尝试按照一个定义良好的转换序列转换，直到有一个成功为止。  如果所选的转换是向上的，则编译器不发出警告。  如果转换是向下的，则编译器发出关于数据可能丢失的警告。  无论实际数据丢失的发生是否取决于实际值，都建议您将此警告视为错误。  如果涉及到用户定义的类型，则编译器尝试使用您在类定义中指定的转换。  如果找不到一个可接受的转换，编译器将发出错误，并停止编译程序。  有关控制标准的转换规则的详细信息，请参阅 [标准转换](../cpp/standard-conversions.md).  有关用户定义的转换的详细信息，请参阅 [用户定义的转换](../dotnet/user-defined-conversions-cpp-cli.md)。  
  
### 扩大转换 \(提升\)  
 在一个扩大转换中，一个较小的变量的值在不丢失数据的情况下赋给一个更大的变量。  由于扩大转换始终是安全的，编译器在不提示的情况下执行它们，且不发出警告。  下面的转换扩大转换。  
  
|从|到|  
|-------|-------|  
|任何带符号或无符号整型类型除 `long long` 和 `__int64`外。|`double`|  
|`bool` 或 `char`|任何其他内置类型|  
|`short` 或 `wchar_t`|`int`, `long`, `long long`|  
|`int`, `long`|`long long`|  
|`float`|`double`|  
  
### 收缩转换 \(强制\)  
 编译器隐式执行收缩转换，但是，它会发出可能丢失数据的警告。  要非常重视这些警告。  如果您确定数据丢失不会发生（因为较小的变量始终可以容纳较大的变量的值），则添加显式强制转换，编译器将不再发出警告。  如果您不确定转换是否安全，请在代码中添加某种运行时检查，以处理可能出现的数据丢失，而确保它不会使程序产生错误的结果。  有关如何处理这些方案的建议，请参见 [如何:收缩转换 \(C\+\+\) 的句柄](http://msdn.microsoft.com/zh-cn/e483237e-501e-4a12-ac24-51526f6ddeaa)。  
  
 任何从浮点类型转换为整型类型都是收缩转换，因为浮点值的部分小数会被丢弃且丢失。  
  
 下面的代码示例演示一些隐式收缩转换和编译器为其发出的警告。  
  
```cpp  
  
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow  
wchar_t wch = 'A'; //OK  
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'  
              // to 'char', possible loss of data  
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from  
                           // 'int' to 'unsigned char'  
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to  
              // 'int', possible loss of data  
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to  
             // 'int', possible loss of data  
  
```  
  
### 有符号 \- 无符号转换  
 有符号整型和它对应的无符号整型的数值部分总是一样大的，但他们值转换的位模式解释是不同的。  下面的代码示例演示的是相同的位模式被解释为有符号值和无符号值时会发生的情况。  存储在 `num` 和 `num2` 的位模式不会像前面例子所展示的那样改变。  
  
```cpp  
  
using namespace std;  
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>  
short num2 = num;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
// Go the other way.  
num2 = -1;  
num = num2;  
cout << "unsigned val = " << num << " signed val = " << num2 << endl;  
// Prints: unsigned val = 65535 signed val = -1  
  
```  
  
 请注意，值在这两个方向中被重新诠释。  如果你的程序会产生奇怪的结果，其中的值的符号似乎与预期的相反，请检查有符号和无符号整数类型之间的隐式转换。  在下面的例子中，当它的存储在`num`时，表达式的结果（0 \- 1）隐式的从 `int` 转换到 `unsigned int`。  这使得位模式被重新解释。  
  
```cpp  
  
unsigned int u3 = 0 - 1;  
cout << u3 << endl; // prints 4294967295  
  
```  
  
 编译器不警告有符号和无符号整数类型之间的隐式转换。  因此，建议您避免有符号和无符号之间的转换。  如果您不能避免它们，然后在您的代码添加运行时检查，以检测选定转换值是否大于等于零或小于等于有符号类型的最大值。  此范围内的值将从有符号数传输到无符号数或从无符号数传输到有符号数，而不必经过重新解释。  
  
### 指针转换  
 在许多表达式，一个C风格的数组隐式把数组的第一个元素转换为一个指针，并且，转换都是悄悄发生的。  虽然此方法很方便，但它也有潜在的错误。  例如，下面的设计不良的代码示例看似荒谬，但它会在Visual C\+\+的编译并生成的结果'p'。  首先，“Help”字符串常量转换为一个指向数组的第一个元素 `char*`类型指针，该指针向后移动3个元素后，指向最后一个元素'P'。  
  
```cpp  
  
char* s = "Help" + 3;  
  
```  
  
## 显式转换（强制转换）  
 使用转换操作，您可以指示编译器将一种类型的值转换为另一种类型。  在某些情况下即使两个类型完全无关，编译器也会引发错误，但是，其他情况下即使操作不是类型安全的，编译器也不会引发错误。  使用强制转换需谨慎，因为从一种类型到另一个类型的任意转换都是程序错误的潜在来源。  但是，强制转换有时是需要的，且不是所有的强制转换都一样危险。  当你的代码执行收缩转换时，并且知道该转换不会使程序产生错误的结果时，强制转换是有效的。  实际上，这是在告诉编译器，你知道你在干什么并且停止用警告干扰你的工作。  另一种强制转换是从派生类指针到指针到基类指针的转换。  另一个强制转换的使用是将 `const` 变量传递给一个需要非 `const` 参数的函数。  大部分强制转换操作都包含一定的风险。  
  
 在 C 样式的程序中，相同 C 样式的强制转换运算符可以为所有强制转换使用。  
  
```cpp  
  
(int) x; // old-style cast, old-style syntax  
int(x); // old-style cast, functional syntax  
  
```  
  
 C 样式的强制转换运算符与运算符 \(\) 一样，因此在代码中不显眼，容易被忽略。  两者都是不好的，因为他们很难一眼就辨认出来或查找出来，并且他们是不同的，可包含`static`, `const`和 `reinterpret_cast`的任意组合。  指出旧式强制转换实际上是困难且容易出错。  基于以上这些原因，当需要强制转换时，我们建议使用下面的 C\+\+ 强制转换运算符之一，在某些情况下，会加强类型安全，且更加明确的表示该程序的目的。  
  
-   `static_cast`，这种强制转换只会在编译时检查。  如果编译器检测到您尝试强制转换完全不兼容的类型，则`static_cast`会返回错误。  您还可以使用它在基类指针和派生类指针之间强制转换，但是，编译器在无法分辨此类转换在运行时是否是安全的。  
  
    ```cpp  
  
    double d = 1.58947;  
    int i = d;  // warning C4244 possible loss of data  
    int j = static_cast<int>(d);       // No warning.  
    string s = static_cast<string>(d); // Error C2440:cannot convert from  
                                       // double to std:string  
  
    // No error but not necessarily safe.  
    Base* b = new Base();  
    Derived* d2 = static_cast<Derived*>(b);  
  
    ```  
  
     有关更多信息，请参见[static\_cast](../cpp/static-cast-operator.md)。  
  
-   为了安全，`dynamic_cast`在运行时检查基类指针和派生类指针之间的强制转换。  `dynamic_cast` 是比 `static_cast` 更安全的强制类型转换，但运行时检查会带来一些开销。  
  
    ```cpp  
  
    Base* b = new Base();  
  
    // Run-time check to determine whether b is actually a Derived*  
    Derived* d3 = dynamic_cast<Derived*>(b);  
  
    // If b was originally a Derived*, then d3 is a valid pointer.  
    if(d3)  
    {  
       // Safe to call Derived method.  
       cout << d3->DoSomethingMore() << endl;  
    }  
    else  
    {  
       // Run-time check failed.  
       cout << "d3 is null" << endl;  
    }  
  
    //Output: d3 is null;  
  
    ```  
  
     有关更多信息，请参见[dynamic\_cast](../cpp/dynamic-cast-operator.md)。  
  
-   将`const_cast`转换为 `const` 的变量，或者将非 `const` 变量转换为 `const`。  通过使用这个操作符强制转换 `const` 就像使用C样式转换一样容易出错，不同之处在于使用 `const-cast` 不太可能意外地执行转换。  有时候你只能强制转换 `const` 的变量，例如，传递 `const` 变量到一个非 `const` 参数的函数中。  下面的示例演示如何执行此操作。  
  
    ```cpp  
  
    void Func(double& d) { ... }  
    void ConstCast()  
    {  
       const double pi = 3.14;  
       Func(const_cast<double&>(pi)); //No error.  
    }  
  
    ```  
  
     有关更多信息，请参见[const\_cast](../cpp/const-cast-operator.md)。  
  
-   `reinterpret_cast`，例如 `pointer` 和 `int`的无关类型的转换。  
  
    > [!NOTE]
    >  此强制转换运算符不是通用的，因此，它不能保证可移植到其它编译器。  
  
     下面的示例演示 `reinterpret_cast` 和 `static_cast` 之间的差异。  
  
    ```cpp  
  
    const char* str = "hello";  
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot  
                                  // convert from 'const char *' to 'int'  
    int j = (int)str; // C-style cast. Did the programmer really intend  
                      // to do this?  
    int k = reinterpret_cast<int>(str);// Programming intent is clear.  
                                       // However, it is not 64-bit safe.  
  
    ```  
  
     有关详细信息，请参阅[reinterpret\_cast 运算符](../cpp/reinterpret-cast-operator.md)。  
  
## 请参阅  
 [C\+\+ 类型系统](../cpp/cpp-type-system-modern-cpp.md)   
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)