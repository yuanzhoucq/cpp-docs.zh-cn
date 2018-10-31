---
title: 一般规则和限制
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 931ae04ef47262f15d037a2b5eeb35bd01a8419d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439219"
---
# <a name="general-rules-and-limitations"></a>一般规则和限制

## <a name="microsoft-specific"></a>Microsoft 专用

- 如果声明函数或对象而无需**dllimport**或**dllexport**属性、 函数或对象不被视为 DLL 接口的一部分。 因此，函数或对象的定义必须存在于该模块或同一程序的另一个模块中。 若要使 DLL 接口的函数或对象一部分，必须声明的函数或作为其他模块中的对象定义**dllexport**。 否则，将生成链接器错误。

   如果声明函数或对象与**dllexport**属性，其定义必须出现在同一程序的某些模块。 否则，将生成链接器错误。

- 如果在程序中的单个模块包含这两**dllimport**并**dllexport**相同的函数或对象，声明**dllexport**特性将优先于通过**dllimport**属性。 但是，会生成编译器警告。 例如：

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- C++ 中，你可以初始化全局声明或静态局部数据指针或与声明的数据对象的地址**dllimport**属性，会生成错误。 在 c。此外，你可以在其中初始化声明的函数与的地址的静态局部函数指针**dllimport**属性。 在 C 中，此类赋值会将指针设置为指向 DLL 导入形式转换 (thunk)（将控制权转交给函数的代码存根）的地址而不是函数的地址。 在 C++ 中，此类赋值会将指针设置为指向函数的地址。 例如：

    ```cpp
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

   但是，因为它包含一个程序**dllexport**中对象的声明的属性必须提供该程序中的某处的对象的定义，可以初始化全局或局部静态函数指针地址**dllexport**函数。 同样，您可以初始化全局或局部静态数据指针的地址**dllexport**数据对象。 例如，以下代码在 C 或 C++ 中不会生成错误：

    ```cpp
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

- 如果将应用**dllexport**拥有未标记为一个基类的常规类**dllexport**，编译器将生成 C4275。

   如果基类是类模板的专用化，则编译器将生成相同的警告。 若要解决此问题，将标记与基类**dllexport**。 类模板的专用化的问题是放置的位置 **__declspec （dllexport)**; 不允许标记类模板。 相反，显式实例化类模板，并将标记与此显式实例化**dllexport**。 例如：

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   如果模板自变量是派生类，则此解决方法将失败。 例如：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   由于这是模板的常见模式，编译器将更改的语义**dllexport**应用于具有一个或多个基类的类的类，以及一个或多个基类是类模板的专用化. 在这种情况下，编译器隐式应用**dllexport**到类模板专用化。 您可以执行以下操作，不会发出警告：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)