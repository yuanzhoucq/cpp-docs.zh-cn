---
title: 线程本地存储 (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 7e308f7ba23503879f8ebbcacde481cf72055229
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510392"
---
# <a name="thread-local-storage-tls"></a>线程本地存储 (TLS)

线程本地存储 (TLS) 是一种方法，给定的多线程进程中的每个线程可以使用这种方法分配用以存储线程特定的数据的位置。 TLS API ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)) 支持动态绑定 (运行时) 线程特定数据。 除了现有的 API C++实现外, Win32 和 Microsoft 编译器现在还支持静态绑定 (加载时) 每线程数据。

## <a name="_core_compiler_implementation_for_tls"></a>TLS 的编译器实现

**C + + 11:** 建议`thread_local`使用存储类说明符来指定对象和类成员的线程本地存储。 有关详细信息, 请参阅[存储类C++()](../cpp/storage-classes-cpp.md)。

MSVC 还提供了特定于 Microsoft 的属性, 即[线程](../cpp/thread.md), 作为扩展存储类修饰符。 使用 **__declspec**关键字声明**线程**变量。 例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>规则和限制

声明静态绑定的线程本地对象和变量时，必须遵守以下准则： 这些准则既适用于[thread](../cpp/thread.md)也适用于[thread_local](../cpp/storage-classes-cpp.md):

- **线程**特性只能应用于类和数据声明和定义。 它不能用于函数声明或定义。 例如，下面的代码生成一个编译器错误：

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- 只能在具有**静态**范围的数据项上指定**线程**修饰符。 这包括全局数据对象 (**静态**和**外部**)、本地静态对象和类的C++静态数据成员。 不能用**thread**特性声明自动数据对象。 以下代码生成编译器错误：

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- 线程本地对象的声明和定义都必须指定**thread**特性。 例如，下面的代码将生成错误：

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **线程**属性不能用作类型修饰符。 例如，下面的代码生成一个编译器错误：

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- 由于允许使用C++ **thread**特性的对象的声明, 因此以下两个示例在语义上是等效的:

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- 线程本地对象的地址不被视为常数, 并且涉及此类地址的任何表达式不会被视为常量表达式。 在标准 C 中, 这种效果是禁止将线程本地变量的地址用作对象或指针的初始值设定项。 例如，C 编译器会将以下代码标记为错误：

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   此限制不适用于C++。 由于 C++ 允许所有对象的动态初始化，可以通过利用使用线程本地变量的地址的表达式将对象初始化。 它的实现方式就像是线程本地对象的构造。 例如, 在将其编译为C++源文件时, 上面显示的代码不会生成错误。 线程本地变量的地址仅在获取了地址的线程仍然存在时有效。

- 标准 C 允许使用涉及对自身的引用的表达式初始化对象或变量, 但只适用于非静态范围的对象。 尽管C++通常允许使用涉及对自身的引用的表达式对对象进行此类动态初始化, 但这种类型的初始化不允许用于线程本地对象。 例如:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   包含要初始化的对象的C++表达式不表示对自身的引用,并在C和中`sizeof`启用。

   C++不允许对线程数据进行这样的动态初始化, 因为将来可能会对线程本地存储设施进行增强。

- 在 windows Vista 之前的 windows 操作系统上`__declspec( thread )` , 有一些限制。 如果 DLL 将任何数据或对象声明为`__declspec( thread )`, 则如果动态加载, 则可能导致保护错误。 在用[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)加载 DLL 后, 只要代码引用`__declspec( thread )`数据, 就会导致系统故障。 由于线程的全局变量空间在运行时进行分配，此空间的大小基于对应用程序的要求加静态链接的所有 DLL 的要求的计算。 使用`LoadLibrary`时, 不能扩展此空间以允许使用`__declspec( thread )`声明的线程本地变量。 如果 DLL 可能使用`LoadLibrary`加载, 请在 DLL 中使用 tls Api (如[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)) 分配 tls。

## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)
