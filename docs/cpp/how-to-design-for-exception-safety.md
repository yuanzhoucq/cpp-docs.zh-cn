---
title: "如何：设计异常安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 19ecc5d4-297d-4c4e-b4f3-4fccab890b3d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：设计异常安全性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

异常结构的优点之一是执行，并在提供有关异常的数据时，直接从该第一个捕获的语句处理它的语句跳转抛出异常。  处理程序可以是任何数量级别的去调用堆栈。  调用 try 语句和 throw 语句不需要任何功能了解有关抛出的异常。但是，它们必须经过专门设计，以便可以超出范围“意外”随时异常可能从下的位置传播，并且这样做，而无需忘记部分已创建的对象、泄漏的内存或在不可用状态的数据结构。  
  
## 基本技术  
 一个可靠的异常处理的策略需要仔细考虑，并且应是设计进程的一部分。  通常，大多数异常在软件模块的较低层被检测并抛出，但是，这些层典型地没有足够的上下文去处理错误，也不对最终用户显示消息。  在中间层，当必须检查异常对象，或是具有额外的有用信息提供给最终捕获异常的上层时，函数可以捕获并再次抛出异常。  只有当异常可以从它完全还原时，函数才应捕获并吞没异常。  在大多数情况下，在中间层的正确的行为是让异常传播调用堆栈。  甚至在最高层，如果该异常使程序处于准确性不能被保证的状态下，允许未经处理的异常终止程序可能适用。  
  
 无论函数如何处理异常，只要能有助于确保“异常安全”，必须基于以下基本规则设计功能处理异常。  
  
### 保持资源类简单  
 当将手动资源管理封装成类时，使用一个只是用来管理每个资源的类；否则，可能产生泄漏。  当可能时，使用 [智能指针](../cpp/smart-pointers-modern-cpp.md)，如以下示例所示。  此示例是有意人工化和简单化得突出当使用 `shared_ptrooooooooooooooooooooooooooooooooooooooooooooooooooooooooo`时的差异。  
  
```cpp  
// old-style new/delete version  
class NDResourceClass {  
private:  
    int*   m_p;  
    float* m_q;  
public:  
    NDResourceClass() : m_p(0), m_q(0) {  
        m_p = new int;  
        m_q = new float;  
    }  
  
    ~NDResourceClass() {  
        delete m_p;  
        delete m_q;  
    }  
    // Potential leak! When a constructor emits an exception,   
    // the destructor will not be invoked.     
};  
  
// shared_ptr version  
#include <memory>  
  
using namespace std;  
  
class SPResourceClass {  
private:  
    shared_ptr<int> m_p;  
    shared_ptr<float> m_q;  
public:  
    SPResourceClass() : m_p(new int), m_q(new float) { }  
    // Implicitly defined dtor is OK for these members,   
    // shared_ptr will clean up and avoid leaks regardless.  
};  
  
// A more powerful case for shared_ptr  
  
class Shape {  
    // ...  
};  
  
class Circle : public Shape {  
    // ...  
};  
  
class Triangle : public Shape {  
    // ...  
};  
  
class SPShapeResourceClass {  
private:  
    shared_ptr<Shape> m_p;  
    shared_ptr<Shape> m_q;  
public:  
    SPShapeResourceClass() : m_p(new Circle), m_q(new Triangle) { }  
};  
  
```  
  
### 使用 RAII 习惯用语管理资源  
 若要是异常安全的，函数必须确保通过使用 `malloc` 或 `new`被分配的对象被销毁，并且，即使抛出异常，所有资源比如文件控键关闭或释放。  *"获取资源即初始化" \(raii\)* \(RAII\) 习惯用语将这些资料的管理关系到自动变量的生存期。  当函数超出范围时，要么通过常规返回；要么因为异常，所有完全构造的自动变量的析构函数被调用。  一个 RAII 包装对象例如智能指针,在其析构函数中调用适当的删除或关闭的功能。  在异常安全的代码中，将每个资源所有权立即更改为 RAII 对象是极其重要的。  请注意`vector`，`string`，`make_shared`，`fstream`，以及相似的类为你处理获取的资源。 但是，`unique_ptr` 和传统的 `shared_ptr` 构造是特定的，因为资源获取由用户执行而不是对象，因此，它们计数，因为 *资源释放属于损坏*，但作为 RAII是有问题的。  
  
## 三个异常确保  
 特别地，异常安全性讨论是根据函数提供的三个例外保护措施：*没有失败的安全保护*、*严格的安全保护*和 *基本的安全保护。*  
  
### 没有失败的安全保护  
 没有失败 \(或，“没有抛出”\) 保护措施是函数可以提供的最严格的安全保护。  指出，该函数不会抛出异常也不允许异常的传播。  但是，不能可靠提供这种保护措施，除非 \(a\) 您知道此函数调用的所有功能也都是没有失败的，或者 \(b\)在其达到此函数之前，您知道抛出的所有异常被捕获，或 \(c\) 您知道如何捕获并正确处理可能达到此函数的所有异常。  
  
 严格的安全保护和基本的安全保护取决于所使用的假设析构函数是没有失败的。  所有标准库中的容器和类型确保其析构函数不抛出安全问题。  还有一个相反的要求：标准库需要为其提供有关的用户定义的类型，例如：作为模板参数——必须具有非抛出的析构函数。  
  
### 严格的安全保护  
 严格的安全保证表明，如果因异常函数超出范围，它将不会泄漏内存，程序状态将不会修改。  提供可靠的安全保护的函数是会提交或回滚语义的基本事务：要么完全成功，要么不会有任何效果。  
  
### 基本的安全保护  
 基本的安全保护是三个保护措施中最弱的。  但是，当严格的安全保护在内存消耗或在性能开销太大时，基本的安全保护可能是最佳选择。  基本的安全保护表明，如果发生异常，内存不会泄漏，并且即使数据可能已被修改，对象仍处于一个可用的状态。  
  
## 异常安全类  
 即使类通过不安全的功能使用，仍可通过阻止部分构造或部分被销毁，帮助确保自己的异常安全。  如果类构造函数在完成之前退出，则对象永远不会被创建，并且其析构函数永远不会被调用。  尽管在异常之前进行自动变量的初始化，将会调用其析构函数，不受智能指针或类似的自动变量托管调用的动态分配的内存或资源将泄漏。  
  
 所有内置类型是没有失败的，并且标准库类型会在最低限度上支持基本的安全保护。  遵循任何用户定义的类型的准则必须是异常安全的：  
  
-   使用智能指针或其他 RAII 类型的包装器管理所有资源。  避免在您的类析构函数的资源管理功能，因为如果构造函数抛出异常，析构函数不会被调用。  但是，如果类是控件资源的专用资源管理器，使用析构函数管理资源是可以接受的。  
  
-   了解基类构造函数抛出的异常在派生类构造函数中是不能被合并的。  如果要转换并再次抛出在派生的构造函数的基类异常，请使用 try 函数块。  有关详细信息，请参阅[如何:在基类构造函数 \(C\+\+\) 的异常](http://msdn.microsoft.com/zh-cn/53bb822e-785b-4581-9517-210dd05060a3)。  
  
-   考虑是否在智能指针所包装的数据成员存储所有类状态，特别是，如果类具有允许失败“初始化"的概念。虽然 C\+\+ 允许使用未初始化的数据成员，但它不支持未初始化或部分初始化的类实例。  构造函数必须是要么成功，要么失败；如果构造函数没有完成运行，就不能创建对象。  
  
-   不允许忽略任何析构函数中的异常。  C\+\+ 的一个基本公理是析构函数不应允许异常传播调用堆栈。  如果析构函数必须执行可能需要异常抛出的操作，则必须在 try\-catch 块中这么做并要吞并异常。  标准库为其定义的所有析构函数提供保证。  
  
## 请参阅  
 [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [如何：异常和非异常代码之间的接口](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)