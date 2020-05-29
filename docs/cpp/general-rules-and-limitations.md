---
title: 一般规则和限制
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 1adbaf9d9be3a0fc0724603e01b81700554839bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188581"
---
# <a name="general-rules-and-limitations"></a>一般规则和限制

**Microsoft 专用**

- 如果在不使用**dllimport**或**dllexport**特性的情况下声明函数或对象，则不会将函数或对象视为 DLL 接口的一部分。 因此，函数或对象的定义必须存在于该模块或同一程序的另一个模块中。 若要使函数或对象成为 DLL 接口的一部分，必须将另一个模块中的函数或对象的定义声明为**dllexport**。 否则，将生成链接器错误。

   如果使用**dllexport**特性声明函数或对象，则其定义必须出现在同一程序的某个模块中。 否则，将生成链接器错误。

- 如果程序中的单个模块包含同一函数或对象的**dllimport**和**dllexport**声明，则**dllexport**特性优先于**dllimport**特性。 但是，会生成编译器警告。 例如：

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- 在C++中，您可以使用使用**dllimport**特性声明的数据对象的地址初始化全局声明或静态本地数据指针，也可以在 C 中生成错误。此外，还可以使用使用**dllimport**特性声明的函数的地址初始化静态本地函数指针。 在 C 中，此类赋值会将指针设置为指向 DLL 导入形式转换 (thunk)（将控制权转交给函数的代码存根）的地址而不是函数的地址。 在 C++ 中，此类赋值会将指针设置为指向函数的地址。 例如：

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

   但是，因为在对象声明中包含**dllexport**特性的程序必须在程序中的某个位置提供该对象的定义，所以，可以使用**dllexport**函数的地址初始化全局或局部静态函数指针。 同样，可以使用**dllexport**数据对象的地址初始化全局或局部静态数据指针。 例如，以下代码在 C 或 C++ 中不会生成错误：

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

- 如果将**dllexport**应用于具有未标记为**dllexport**的基类的常规类，则编译器将生成 C4275。

   如果基类是类模板的专用化，则编译器将生成相同的警告。 若要解决此情况，请使用**dllexport**标记基类。 类模板专用化的问题是放置 **__declspec （dllexport）** 的位置;不允许标记类模板。 相反，显式实例化类模板，并将此显式实例化标记为**dllexport**。 例如：

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

   由于这是带有模板的常见模式，因此当应用于具有一个或多个基类的类以及一个或多个基类是类模板的专用化时，编译器会更改**dllexport**的语义。 在这种情况下，编译器会将**dllexport**隐式应用于类模板的专用化。 你可以执行以下操作，而不会收到警告：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
