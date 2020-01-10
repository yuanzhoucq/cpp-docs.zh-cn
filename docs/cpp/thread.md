---
title: thread
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: cc21602764a9a3c2584bdd7da62c75974ffdd5fb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301283"
---
# <a name="thread"></a>thread

**Microsoft 专用**

**线程**扩展存储类修饰符用于声明线程局部变量。 对于可移植等效的 C++ 11 及更高版本，使用[thread_local](../cpp/storage-classes-cpp.md#thread_local)对于可移植代码的存储类说明符。 在 Windows **thread_local**上通过 **__declspec （thread）** 来实现。

## <a name="syntax"></a>语法

**__declspec （thread）** *声明符*

## <a name="remarks"></a>备注

线程本地存储 (TLS) 是多线程进程中的每个线程为线程特定的数据分配存储时所采用的机制。 在标准多线程程序中，数据在给定进程的所有线程间共享，而线程本地存储是用于分配每个线程数据的机制。 有关线程的完整讨论，请参阅[多线程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

线程局部变量的声明必须将[扩展的特性语法](../cpp/declspec.md)和 **__declspec**关键字与**thread**关键字一起使用。 例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：

```cpp
__declspec( thread ) int tls_i = 1;
```

在动态加载的库中使用线程本地变量时，需要注意可能导致无法正确初始化线程本地变量的因素：

1. 如果使用函数调用（包括构造函数）对变量进行初始化，则仅对导致二进制/DLL 加载到进程中的线程以及在加载二进制/DLL 之后启动的线程调用此函数。 加载 DLL 时，不会为已在运行的任何其他线程调用初始化函数。 动态初始化发生在 DLL_THREAD_ATTACH 的 DllMain 调用上，但如果该 DLL 在线程启动时不在进程中，则 DLL 永远不会获取该消息。

1. 以静态方式初始化的线程本地变量通常在所有线程上都已正确初始化。 不过，从2017年12月起，Microsoft C++编译器会出现已知的一致性问题，让**constexpr**变量接收动态和静态初始化。

   注意：这两个问题都应在以后的编译器更新中得到解决。

此外，声明线程本地对象和变量时必须遵守以下准则：

- 只能将**thread**特性应用于类和数据声明和定义;**线程**不能用于函数声明或定义。

- 只能在具有静态存储持续时间的数据项上指定**thread**特性。 这包括全局数据对象（**静态**和**外部**）、本地静态对象和类的静态数据成员。 不能用**thread**特性声明自动数据对象。

- 无论声明和定义是出现在同一文件中还是单独的文件中，都必须为声明和线程本地对象定义使用**thread**特性。

- 不能将**thread**特性用作类型修饰符。

- 由于允许使用**thread**特性的对象的声明，这两个示例在语义上是等效的：

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- 标准 C 允许使用涉及对自身的引用的表达式（但仅适用于非静态对象）初始化对象或变量。 尽管C++通常允许使用涉及对自身的引用的表达式对对象进行这样的动态初始化，但这种类型的初始化不允许用于线程本地对象。 例如：

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   包含要初始化的对象的**sizeof**表达式不构成对自身的引用，并允许在 C 和C++中使用。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[线程本地存储 (TLS)](../parallel/thread-local-storage-tls.md)