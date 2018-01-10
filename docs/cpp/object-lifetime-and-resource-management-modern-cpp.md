---
title: "对象生存期和资源管理 （现代 c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e2b48630fab9d27bf5db442617a5184bd26de5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>对象生存期和资源管理（现代 C++）
与托管语言不同，C++ 没有垃圾回收 (GC)，垃圾回收将在程序运行时自动释放不再使用的内存资源。 在 C++ 中，资源管理直接与对象生存期相关。 本文档描述影响 C++ 中对象生存期的因素以及如何管理对象生存期。  
  
 C++ 没有 GC 的主要原因是它不会处理非内存资源。 仅类似 C++ 中的确定析构函数可公平处理内存和非内存资源。 GC 还有其他问题，类似更高的内存和 CPU 使用率开销以及区域。 但是，普遍是无法通过机智的优化迁移的基础问题。  
  
## <a name="concepts"></a>概念  
 对象生存期管理中一个重要的事项是封装 - 使用对象不必知道对象拥有的资源，或如何摆脱资源，或者甚至它是否拥有任何资源。 它只需销毁对象即可。 C++ 核心语言旨在确保在正确的时间（即，当块退出时）以构造的倒序销毁对象。 销毁对象时，将按特定顺序销毁其基项和成员。  除非您进行诸如堆分配或放置新对象等特殊操作，否则此语言将自动销毁对象。  例如，[智能指针](../cpp/smart-pointers-modern-cpp.md)如`unique_ptr`和`shared_ptr`，和 c + + 标准库容器类似`vector`，封装`new` / `delete`和`new[]` /`delete[]`在对象中，具有析构函数。 这就是为什么因此，务必使用智能指针和 c + + 标准库容器。  
  
 生存期管理中另一个重要概念：析构函数。 析构函数封装资源释放。  （常用的助记键是 RRID，资源释放是析构。）资源是您从“系统”中获取并且之后必须归还的内容。  内存是最常见的资源，但还有文件、套接字、纹理和其他非内存资源。 “拥有”资源意味着您可以在需要时使用资源，但还必须在用完时释放。  销毁对象时，其析构函数将释放它拥有的资源。  
  
 最终概念是 DAG（定向非循环图形）。  程序的所有权结构构成 DAG。 无对象能拥有自身 - 不仅不可能而且本质上无意义。 但是两个对象可以共享第三个对象的所有权。  DAG 中可能存在的许多链接类型与下类似：A 是 B 的成员（B 拥有 A），C 存储 `vector<D>`（C 拥有每个 D 元素），E 存储 `shared_ptr<F>`（E 可能与其他对象一起共享 F 的所有权），以此类推。  只要没有循环，DAG 中的每个链接就将由具有析构函数（而不是原始指针、句柄或其他机制）的对象表示，然后不可能出现资源泄漏，因为此语言阻止泄漏。 在没有垃圾回收器运行的情况下，在不再需要资源后立即将其释放。 堆栈范围、基项、成员和相关案例的生存期跟踪无开销，而 `shared_ptr` 的生存期跟踪很便宜。  
  
### <a name="heap-based-lifetime"></a>基于堆的生存期  
 对于堆对象生存期，使用[智能指针](../cpp/smart-pointers-modern-cpp.md)。 将 `shared_ptr` 和 `make_shared` 分别用作默认指针和分配器。 使用 `weak_ptr` 中断循环、执行缓存并观察对象，而不影响或假定有关其生存期的任何内容。  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 使用`unique_ptr`为了唯一所有权，例如，在*pimpl*惯用语法。 (请参阅[用于编译时封装的 Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)。)使 `unique_ptr` 成为所有显式 `new` 表达式的主要目标。  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 您可以为非所有权和观察使用原始指针。 非拥有指针可能悬挂，但不会泄漏。  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 需要性能优化时，你可能必须使用*完好封装*拥有指针和显式调用来删除。 例如，在实现自己的低级别数据结构时。  
  
### <a name="stack-based-lifetime"></a>基于堆栈的生存期  
 在现代 c + +，*基于堆栈的范围*是一种强大的方法，因为它将结合自动编写可靠代码*堆栈生存期*和*数据成员生存期*，同时高效-生存期跟踪绝对无开销。 堆对象生存期需要努力的手动管理，可能是资源泄露和无效的根源，尤其是在您使用原始指针时。 考虑此代码，其演示了基于堆栈的范围：  
  
```cpp  
class widget {  
private:  
    gadget g;   // lifetime automatically tied to enclosing object  
public:  
    void draw();  
};  
  
void functionUsingWidget () {  
    widget w;   // lifetime automatically tied to enclosing scope  
                // constructs w, including the w.g gadget member  
    // ...
    w.draw();  
    // ...
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
```  
  
 慎用静态生存期（全局静态、函数全局静态），因为可能出现问题。 当全局对象的构造函数引发异常时，会发生什么情况？ 通常，应用程序的故障出在难以调试的方式。 构造顺序是静态生存期对象的问题，并且不是并发安全的。 不仅对象构造是个问题，析构顺序可能会很复杂，特别是涉及多形性时。 即使对象或变量不是多形性的，并且没有复杂的构造/销毁顺序，仍然存在线程安全并发问题。 在没有线程本地存储、资源锁定和其他特殊预防措施的情况下，多线程应用程序无法安全地修改静态对象的数据。  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)