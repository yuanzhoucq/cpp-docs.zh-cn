---
title: "线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_cpp
dev_langs:
- C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8c514879368b8ea3d676635f2b922a2e1c07224
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="thread"></a>thread

**Microsoft 专用**

**线程**扩展的存储类修饰符用于声明线程本地变量。 对于可移植等效的 C++ 11 及更高版本，使用[thread_local](../cpp/storage-classes-cpp.md#thread_local)对于可移植代码的存储类说明符。 在 Windows 上**thread_local**通过实现**__declspec （thread)**。

## <a name="syntax"></a>语法

> **__declspec( thread )** *declarator*  

## <a name="remarks"></a>备注

线程本地存储 (TLS) 是多线程进程中的每个线程为线程特定的数据分配存储时所采用的机制。 在标准多线程程序中，数据在给定进程的所有线程间共享，而线程本地存储是用于分配每个线程数据的机制。 有关线程的完整讨论，请参阅[多线程处理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

线程局部变量的声明必须使用[扩展特性语法](../cpp/declspec.md)和`__declspec`关键字后的跟**线程**关键字。 例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：

```cpp
__declspec( thread ) int tls_i = 1;
```

动态加载库中使用线程本地变量，需要注意的因素可能会导致不会正确初始化线程本地变量：

1. 如果函数调用 （包括构造函数） 在初始化变量时，此函数将仅调用线程导致二进制/DLL 以加载到进程中，以及二进制/DLL 已加载后启动这些线程。 为已在运行时已加载该 DLL 的其他任何线程不调用初始化函数。 动态初始化永远不会获取消息如果线程启动时，DLL 不在过程上 DLL_THREAD_ATTACH，DllMain 调用，但该 DLL 时发生。

1. 使用常量的值以静态方式初始化线程本地变量通常在所有线程上正确初始化。 但是，自 2017 年 12 月起时会出现已知的一致性问题凭此 constexpr 变量接收的 Microsoft Visual C++ 编译器中动态而不是静态初始化。

   注意： 这两个这些问题被需要修复在将来的编译器的更新。

此外，在声明线程本地对象和变量时必须遵守下列准则：

- 你可以将应用**线程**属性仅为类和数据声明和定义;**线程**不能用于函数声明或定义。

- 你可以指定**线程**只能在具有静态存储持续时间的数据项上的属性。 这包括全局数据对象 (同时**静态**和**extern**)，本地静态对象和类的静态数据成员。 你不能声明自动数据对象与**线程**属性。

- 必须使用**线程**是否声明和定义出现在同一文件中还是单独的文件属性，则为声明和定义的线程本地对象。

- 不能使用**线程**用作类型修饰符的属性。

- 因为使用的对象的声明**线程**允许属性，这两个示例在语义上等效：

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

- 标准 C 允许使用涉及引用自身的表达式初始化对象或变量，但只适用于非静态范围的对象。 虽然 C++ 通常允许使用涉及引用自身的表达式动态初始化对象，但是不允许将这种类型的初始化用于线程本地对象。 例如:

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

[__declspec](../cpp/declspec.md)  
[关键字](../cpp/keywords-cpp.md)  
[线程本地存储 (TLS)](../parallel/thread-local-storage-tls.md)  
