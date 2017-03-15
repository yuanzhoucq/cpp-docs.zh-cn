---
title: "线程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "thread"
  - "thread_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], 线程"
  - "thread __declspec 关键字"
  - "线程本地存储 (TLS)"
  - "TLS（线程本地存储）, 编译器实现"
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 线程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 **thread** 扩展存储类修饰符用于声明线程局部变量。  对于 C\+\+11 中的可移植等效，使用 [thread\_local](../cpp/storage-classes-cpp.md#thread_local) 存储类说明符。  
  
## 语法  
  
```  
  
__declspec( thread ) declarator  
```  
  
## 备注  
 线程本地存储 \(TLS\) 是多线程进程中的每个线程为线程特定的数据分配存储时所采用的机制。  在标准多线程程序中，数据在给定进程的所有线程间共享，而线程本地存储是用于分配每个线程数据的机制。  有关线程的完整讨论，请参阅[多线程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 线程局部变量的声明必须将[扩展的特性语法](../cpp/declspec.md)与 `__declspec` 关键字和 **thread** 关键字一起使用。  例如，以下代码声明了一个整数线程局部变量，并用一个值对其进行初始化：  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 在声明线程局部对象和变量时必须遵守下列准则：  
  
-   可以只将 **thread** 特性应用于类和数据声明和定义；**thread** 不能用于函数声明或定义。  
  
-   使用 **thread** 特性可能会影响 DLL 导入的[延迟加载](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**  
  
-   在 XP 系统上，如果 DLL 使用 \_\_declspec \(thread\) 数据并且通过 LoadLibrary 动态加载而成，则 `thread` 可能无法正常运行。  
  
-   只能在具有静态存储持续时间的数据项上指定 **thread** 特性。  这包括全局数据对象（**static** 和 `extern`）、本地静态对象和类的静态数据成员。  不能声明带 **thread** 特性的自动数据对象。  
  
-   必须为线程本地对象的声明和定义使用 **thread** 特性，无论声明和定义是在同一文件中还是单独的文件中发生。  
  
-   无法将 **thread** 特性用作类型修饰符。  
  
-   由于允许使用 **thread** 特性的对象的声明，因此下面的两个示例在语义上是等效的：  
  
    ```  
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
  
-   标准 C 允许使用涉及引用自身的表达式初始化对象或变量，但只适用于非静态范围的对象。  虽然 C\+\+ 通常允许使用涉及引用自身的表达式动态初始化对象，但是不允许将这种类型的初始化用于线程本地对象。  例如:  
  
    ```  
    // declspec_thread_3.cpp  
    // compile with: /LD  
    #define Thread __declspec( thread )  
    int j = j;   // Okay in C++; C error  
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++  
    ```  
  
     请注意，包含将初始化的对象的 `sizeof` 表达式不构成对自身的引用，允许在 C 和 C\+\+ 中使用该表达式。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [线程本地存储 \(TLS\)](../parallel/thread-local-storage-tls.md)