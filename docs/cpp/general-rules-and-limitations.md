---
title: 一般规则和限制
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 8d21f627f461dce90af93ca5c1af8c4a28098539
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213406"
---
# <a name="general-rules-and-limitations"></a>一般规则和限制

**Microsoft 专用**

- 如果在不使用或特性的情况下声明函数或对象 **`dllimport`** **`dllexport`** ，则不会将函数或对象视为 DLL 接口的一部分。 因此，函数或对象的定义必须存在于该模块或同一程序的另一个模块中。 若要使函数或对象成为 DLL 接口的一部分，必须将另一个模块中的函数或对象的定义声明为 **`dllexport`** 。 否则，将生成链接器错误。

   如果使用属性声明函数或对象，则 **`dllexport`** 其定义必须出现在同一程序的某个模块中。 否则，将生成链接器错误。

- 如果程序中的单个模块包含 **`dllimport`** **`dllexport`** 同一函数或对象的 and 声明，则该 **`dllexport`** 属性优先于 **`dllimport`** 属性。 但是，会生成编译器警告。 例如：

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- 在 c + + 中，可以使用属性声明的数据对象的地址初始化全局声明或静态本地数据指针，也可以在 **`dllimport`** c 中生成错误。此外，还可以使用属性声明的函数的地址初始化静态本地函数指针 **`dllimport`** 。 在 C 中，此类赋值会将指针设置为指向 DLL 导入形式转换 (thunk)（将控制权转交给函数的代码存根）的地址而不是函数的地址。 在 C++ 中，此类赋值会将指针设置为指向函数的地址。 例如：

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

   但是，由于包含 **`dllexport`** 对象声明中的特性的程序必须在程序中的某个位置提供该对象的定义，因此可以使用函数的地址初始化全局或局部静态函数指针 **`dllexport`** 。 同样，可以使用数据对象的地址初始化全局或局部静态数据指针 **`dllexport`** 。 例如，以下代码在 C 或 C++ 中不会生成错误：

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

- 如果将应用于 **`dllexport`** 具有未标记为的基类的常规类 **`dllexport`** ，则编译器将生成 C4275。

   如果基类是类模板的专用化，则编译器将生成相同的警告。 若要解决此情况，请使用标记基类 **`dllexport`** 。 类模板专用化的问题是放置的位置 **`__declspec(dllexport)`** ; 不允许标记类模板。 相反，显式实例化类模板，并将此显式实例化标记为 **`dllexport`** 。 例如：

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

   由于这是带有模板的常见模式，因此 **`dllexport`** 当应用于具有一个或多个基类的类时，以及当一个或多个基类是类模板的专用化时，编译器会更改的语义。 在这种情况下，编译器将隐式应用于 **`dllexport`** 类模板的专用化。 你可以执行以下操作，而不会收到警告：

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[dllexport、dllimport](../cpp/dllexport-dllimport.md)
