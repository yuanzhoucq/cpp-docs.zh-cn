---
title: "常规规则和限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 常规规则和限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
  
-   如果在不使用 **dllimport** 或 `dllexport` 特性的情况下声明函数或对象，则该函数或对象不会被视为 DLL 接口的一部分。  因此，函数或对象的定义必须存在于该模块或同一程序的另一个模块中。  若要使函数或对象成为 DLL 接口的一部分，您必须将其他模块中函数或对象的定义声明为 `dllexport`。  否则，将生成链接器错误。  
  
     如果使用 `dllexport` 特性声明函数或对象，则其定义必须出现在同一程序的某个模块中。  否则，将生成链接器错误。  
  
-   如果您程序中的单个模块包含同一函数或对象的 **dllimport** 和 `dllexport` 声明，则 `dllexport` 特性将优先于 **dllimport** 特性。  但是，会生成编译器警告。  例如：  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   在 C\+\+ 中，您可初始化全局声明的局部数据指针或静态局部数据指针，或利用使用 **dllimport** 特性声明的数据对象的地址进行初始化，后一种初始化方法在 C 中会生成错误。  此外，您还可利用使用 **dllimport** 特性声明的函数的地址初始化静态局部函数指针。  在 C 中，此类赋值会将指针设置为指向 DLL 导入形式转换 \(thunk\)（将控制权转交给函数的代码存根）的地址而不是函数的地址。  在 C\+\+ 中，此类赋值会将指针设置为指向函数的地址。  例如：  
  
    ```  
    __declspec( dllimport ) void func1( void );  
    __declspec( dllimport ) int i;  
  
    int *pi = &i;                             // Error in C  
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,  
                                              // function in C++  
  
    void func2()  
    {  
       static int *pi = &i;                  // Error in C  
       static void ( *pf )( void ) = &func1; // Address of thunk in C,  
                                             // function in C++  
    }  
    ```  
  
     但是，由于包含对象声明中的 `dllexport` 特性的程序必须在程序中某个位置为对象提供定义，因此您可以利用 `dllexport` 函数的地址初始化全局或局部静态函数指针。  同样，您可以利用 `dllexport` 数据对象的地址初始化全局或局部静态数据指针。  例如，以下代码在 C 或 C\+\+ 中不会生成错误：  
  
    ```  
    __declspec( dllexport ) void func1( void );  
    __declspec( dllexport ) int i;  
  
    int *pi = &i;                              // Okay  
    static void ( *pf )( void ) = &func1;      // Okay  
  
    void func2()  
    {  
        static int *pi = &i;                   // Okay  
        static void ( *pf )( void ) = &func1;  // Okay  
    }  
    ```  
  
-   由于 Visual C\+\+ .NET 中引入的行为更改使 `dllexport` 在常规类和类模板专用化之间的应用更一致，因此如果您将 `dllexport` 应用于具有未标记为 `dllexport` 的基类的常规类，则编译器将生成 C4275。  
  
     如果基类是类模板的专用化，则编译器将生成相同的警告。  若要解决此问题，请将基类标记为 `dllexport`。  类模板专用化的问题在于在何处放置 **\_\_declspec\(dllexport\)**；不允许标记类模板。  相反，应显式实例化类模板并将此显式实例化标记为 `dllexport`。  例如：  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     如果模板参数是派生类，则此解决方法将失败。  例如：  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     由于这是模板的常见模式，因此当 `dllexport` 应用于具有一个或多个基类的类时，以及一个或多个基类是类模板的专用化时，编译器将更改该特性的语义。  在这种情况下，编译器会将 `dllexport` 隐式应用于类模板的专用化。  在 Visual C\+\+ .NET 中，用户可执行以下代码而不会收到警告：  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)