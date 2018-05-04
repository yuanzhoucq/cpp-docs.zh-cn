---
title: 线程本地存储 (TLS) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b01bd50fa50a449128842755898d703f7bafe76
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="thread-local-storage-tls"></a>线程本地存储 (TLS)
线程本地存储 (TLS) 是一种方法，给定的多线程进程中的每个线程可以使用这种方法分配用以存储线程特定的数据的位置。 动态绑定 （运行时） 线程特定的数据支持 TLS api ([TlsAlloc](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686801)， [TlsGetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686812)， [TlsSetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686818)，和[TlsFree](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686804)). 有关如何在 Windows 上实现线程本地存储区的详细信息，请参阅[线程本地存储 (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx)。  Win32 和 Visual C++ 编译器现在除了支持现有的 API 实现外，还支持静态绑定（负载时）每线程数据。  
  
##  <a name="_core_compiler_implementation_for_tls"></a> TLS 的编译器实现  
 **C + + 11:** `thread_local`存储类说明符是指定对象的线程本地存储和类成员的建议的方法。 有关详细信息，请参阅[存储类 （c + +）](../cpp/storage-classes-cpp.md)。  
  
 Visual c + + 还提供了特定于 Microsoft 的特性，[线程](../cpp/thread.md)，作为扩展的存储类修饰符。 使用`__declspec`关键字来声明**线程**变量。 例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>规则和限制  
 声明静态绑定的线程本地对象和变量时，必须遵守以下准则： 这些准则同时适用于[线程](../cpp/thread.md)并在大多数情况下还对其[thread_local](../cpp/storage-classes-cpp.md):  
  
-   `thread` 特性仅可适用于类以及数据声明和定义。 它不能用于函数声明或定义。 例如，下面的代码生成一个编译器错误：  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   在具有 `static` 盘区的数据项上才可能指定 `thread` 修饰符。 这包括全局数据对象（`static` 和 `extern`）、本地静态对象和 C++ 类的静态数据成员。 不能使用 `thread` 特性声明自动数据对象。 以下代码生成编译器错误：  
  
    ```  
  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
-   线程本地对象的所有声明和定义必须全部指定 `thread` 特性。 例如，下面的代码将生成错误：  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   `thread` 特性不能用作类型修饰符。 例如，下面的代码生成一个编译器错误：  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   由于允许执行使用 `thread` 特性的 C++ 对象的声明，因此以下两个示例在语义上是等效的：  
  
    ```  
  
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
  
-   线程本地对象的地址不视为常数，并且涉及此类地址的任何表达式不会被视为常量表达式。 在标准 C 中，此操作的效果是禁止将线程本地变量的地址用作对象或指针的初始值设定项。 例如，C 编译器会将以下代码标记为错误：  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     此限制在 C++ 中不适用。 由于 C++ 允许所有对象的动态初始化，可以通过利用使用线程本地变量的地址的表达式将对象初始化。 就像完成线程本地对象的构造一样完成此操作。 例如，当编译成 C++ 源文件时，前面所示的代码不生成错误。 请注意，仅当从中获取地址的线程仍然存在时，线程本地变量的地址才有效。  
  
-   标准 C 允许使用涉及引用自身的表达式进行对象或变量的初始化，但只适用于非静态范围的对象。 虽然 C++ 通常允许使用涉及引用自身的表达式进行此类的对象动态初始化，但是不允许对线程本地对象进行这种初始化。 例如：  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     请注意，包含正在初始化的对象的 `sizeof` 表达式，不表示对自身的引用，并在 C 和 C++ 中都启用。  
  
     因为将来可能要对线程本地存储功能进行增强，C++ 不允许对线程数据进行此类的动态初始化。  
  
-   在 Windows Vista 之前的 Windows 操作系统上`__declspec`（线程） 具有一些限制。 如果 DLL 将任何数据或对象声明为 `__declspec`（线程），可能会导致保护错误（如果动态加载）。 与加载该 DLL 后[LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)，它会导致系统故障，只要代码引用`__declspec`（线程） 数据。 由于线程的全局变量空间在运行时进行分配，此空间的大小基于对应用程序的需求加静态链接的所有 DLL 的需求的计算。 使用 `LoadLibrary` 时，不能扩展此空间以允许用 `__declspec`（线程）声明的线程本地变量。 使用 TLS Api，如[TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)，DLL 来分配 TLS，如果可能与加载该 DLL 中`LoadLibrary`。  
  
## <a name="see-also"></a>请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)   
