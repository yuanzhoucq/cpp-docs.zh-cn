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
ms.openlocfilehash: 59a1af8a7eb73207f84ddf2194d5fe9e77d7d46a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221960"
---
# <a name="thread"></a>thread

**Microsoft 专用**

**线程**扩展的存储类修饰符用于声明线程本地变量。 对于可移植等效的 C++ 11 及更高版本，使用[thread_local](../cpp/storage-classes-cpp.md#thread_local)对于可移植代码的存储类说明符。 在 Windows 上`thread_local`通过实现 **__declspec （thread)**。

## <a name="syntax"></a>语法

> **__declspec( thread )** *declarator*

## <a name="remarks"></a>备注

线程本地存储 (TLS) 是多线程进程中的每个线程为线程特定的数据分配存储时所采用的机制。 在标准多线程程序中，数据在给定进程的所有线程间共享，而线程本地存储是用于分配每个线程数据的机制。 有关线程的完整讨论，请参阅[多线程处理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

必须使用线程本地变量的声明[扩展特性语法](../cpp/declspec.md)并 **__declspec**关键字**线程**关键字。 例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：

```cpp
__declspec( thread ) int tls_i = 1;
```

在动态加载的库中使用线程本地变量，需要注意的因素可能会导致为正确初始化的线程本地变量：

1. 如果通过函数调用 （包括构造函数） 初始化变量，此函数将只调用导致二进制/DLL 加载到进程的线程和二进制文件/DLL 已加载后启动这些线程。 为已在运行时加载该 DLL 的其他任何线程不调用初始化函数。 动态初始化永远不会获取该消息 DLL 不是在过程中，在线程启动时如果 DLL_THREAD_ATTACH，DllMain 调用，但在 DLL 上发生。

1. 使用常量值以静态方式初始化的线程本地变量通常在所有线程上正确初始化。 但是，截至 2017 年 12 月没有已知的符合性问题在 microsoftC++编译器来接收动态而不是静态初始化的 constexpr 变量。

   注意:这两个问题需要解决在将来的编译器更新。

此外，声明线程本地对象和变量时必须遵守以下准则：

- 您可以将应用**线程**属性仅对类和数据声明和定义;**线程**不能用于函数声明或定义。

- 您可以指定**线程**属性只能在具有静态存储持续时间的数据项上。 这包括全局数据对象 (同时**静态**并**extern**)，本地静态对象和类的静态数据成员。 不能声明自动数据对象与**线程**属性。

- 必须使用**线程**属性的声明和线程本地对象，定义是否声明和定义是出现在同一个文件或单独的文件中。

- 不能使用**线程**用作类型修饰符的属性。

- 因为使用的对象的声明**线程**允许特性，这两个示例在语义上等效：

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

- 标准 C 允许使用涉及引用自身的表达式初始化对象或变量，但只适用于非静态范围的对象。 虽然 C++ 通常允许使用涉及引用自身的表达式动态初始化对象，但是不允许将这种类型的初始化用于线程本地对象。 例如：

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   请注意， **sizeof**包含正在初始化的对象的表达式不构成对自身的引用，允许 C 和 C++ 中。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[线程本地存储 (TLS)](../parallel/thread-local-storage-tls.md)