---
title: "constexpr (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "constexpr"
  - "constexpr_cpp"
dev_langs: 
  - "C++"
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# constexpr (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

关键字 `constexpr` 于 C\+\+11 中引入并于 C\+\+14 中得到改善。  它表示*常数表达式*。  与 `const` 相同，它可应用于变量，因此如果任何代码试图修改该值，均将引发编译器错误。  与 `const` 不同，`constexpr` 也可应用于函数和类构造函数。  `constexpr` 指示值或返回值是常数，并且如果可能，将在编译时计算值或返回值。  每当需要 const 整数时（如在模板参数和数组声明中），均可使用 `constexpr` 整数值。  当可以在编译时（而非运行时）计算某个值时，它可以使程序运行速度更快、占用内存更少。  
  
## 语法  
  
```vb  
  
constexpr  literal-type  identifier = constant-expression;  
constexpr  literal-type  identifier { constant-expression };  
constexpr literal-type identifier(params );  
constexpr ctor (params);  
```  
  
#### 参数  
 `params`  
 一个或多个参数必须为文本类型（如下所列），并且其本身必须为常数表达式。  
  
## 返回值  
 一个 constexpr 变量或函数必须返回一个文本类型，如下所列。  
  
## 文本类型  
 为限制计算编译时常量的复杂性及其编译时间的潜在影响，C\+\+14 标准要求常数表达式中所涉及的类型限定为文本类型。  文本类型是可在编译时确定其布局的类型。  以下均为文本类型：  
  
1.  void  
  
2.  标量类型  
  
3.  引用  
  
4.  Void、标量类型或引用的数组  
  
5.  具有普通析构函数以及一个或多个 constexpr 构造函数且不移动或复制构造函数的类。  此外，其所有非静态数据成员和基类必须是文本类型且不可变。  
  
## constexpr 变量  
 Const 和 constexpr 变量之间的主要区别在于：const 变量的初始化可以延迟到运行时，而 constexpr 变量必须在编译时进行初始化。  所有 constexpr 变量均为常量。  
  
```  
constexpr float x = 42.0;  
constexpr float y{108};  
constexpr float z = exp(5, 3);  
constexpr int i; // Error! Not initialized  
int j = 0;  
constexpr int k = j + 1; //Error! j not a constant expression  
```  
  
## constexpr 函数  
 `constexpr` 函数是在使用需要它的代码时，可以在编译时计算其返回值的函数。  `constexpr` 函数必须只接受并返回文本类型。  当其参数为 `constexpr` 值并且在编译时使用代码需要返回值时（例如，初始化一个 `constexpr` 变量或提供一个非类型模板参数），它会生成编译时常量。  使用非`constexpr` 参数调用时，或编译时不需要其值时，它将与正则函数一样，在运行时生成一个值。  （此双重行为使你无需编写同一函数的 `constexpr` 和非 `constexpr` 版本。）  
  
```  
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
```  
  
> [!TIP]
>  注意：在 Visual Studio 调试器中，你可以看出 `constexpr` 函数是否是通过在其内部放置一个断点在编译时计算的。  如果命中该断点，则在运行时调用该函数。  如果未命中，则在编译时调用该函数。  
  
## 一般 constexpr 规则  
 对于要定义为 `constexpr` 的函数、变量、构造函数或静态数据成员，必须满足某些要求：  
  
-   `constexpr` 函数可以是递归的。  它不能是[虚拟的](../cpp/virtual-cpp.md)，并且其返回类型和参数类型必须全部是文本类型。  主体可以定义为 `= default` 或 `= delete`。  否则，必须遵循下列规则：它不包含任何为非文本类型或者为静态或线程本地的 `goto` 语句，try 块、未初始化的变量或变量定义。  此外，如果封闭类具有任何虚拟基类，那么构造函数不能定义为 constexpr。  
  
-   如果一个变量具有文本类型并且未被初始化，则可以使用 `constexpr` 声明该变量。  如果由构造函数执行初始化，则必须将构造函数声明为 `constexpr`。  
  
-   如果所引用的对象已由常数表达式初始化，并且在初始化期间所调用的任何隐式转换也均是常数表达式，则可能将引用声明为 constexpr。  
  
-   所有 `constexpr` 变量或函数的声明都必须具有 `constexpr` 说明符。  
  
-   可以将非 constexpr 模板的显式专用化声明为 `constexpr`：  
  
-   `constexpr` 模板的显式专用化不需要也是 `constexpr`：  
  
-   `constexpr` 函数或构造函数是隐式 `inline`。  
  
## 示例  
 下面的示例演示 `constexpr` 变量、函数和用户定义的类型。  请注意，main \(\) 中的最后一个语句 `constexpr` 成员函数 GetValue\(\) 是运行时调用，因为不需要在编译时已知该值。  
  
```  
#include <iostream>  
  
using namespace std;  
  
// Pass by value   
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
  
// Pass by reference  
constexpr float exp2(const float& x, const int& n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp2(x * x, n / 2) :  
        exp2(x * x, (n - 1) / 2) * x;  
};  
  
// Compile time computation of array length  
template<typename T, int N>  
constexpr int length(const T(&ary)[N])   
{   
    return N;   
}   
  
// Recursive constexpr function  
constexpr int fac(int n)  
{   
    return n == 1 ? 1 : n*fac(n - 1);   
}  
  
// User-defined type  
class Foo  
{  
public:  
    constexpr explicit Foo(int i) : _i(i) {}  
    constexpr int GetValue()  
    {  
        return _i;  
    }  
private:  
    int _i;  
};  
  
int main()  
{  
    //foo is const:  
    constexpr Foo foo(5);   
    // foo = Foo(6); //Error!  
  
    //Compile time:  
    constexpr float x = exp(5, 3);   
    constexpr float y { exp(2, 5) };  
    constexpr int val = foo.GetValue();   
    constexpr int f5 = fac(5);  
    const int nums[] { 1, 2, 3, 4 };  
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };  
  
    //Run time:   
    cout << "The value of foo is " << foo.GetValue() << endl;   
  
}  
  
```  
  
## 要求  
 Visual Studio 2015  
  
## 请参阅  
 [声明和定义](../cpp/declarations-and-definitions-cpp.md)   
 [const](../cpp/constexpr-cpp.md)