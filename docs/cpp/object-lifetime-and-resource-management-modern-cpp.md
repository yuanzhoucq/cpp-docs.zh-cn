---
title: "对象生存期和资源管理（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对象生存期和资源管理（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与托管 C\+\+ 语言，没有垃圾回收 \(GC\)，自动释放非使用长的内存资源，当程序运行。  在 C\+\+ 中，直接管理资源与对象生存期。  文档描述影响 C\+\+ 中的对象生存期和如何管理它的因素。  
  
 Main，因为它不会处理非内存资源，C\+\+ 没有 GC。  类似这些的仅确定性的析构函数在 C\+\+ 中平均处理内存和非内存资源。  GC 还有其他问题，类似更高的开销。内存和 CPU 使用率和位置。  但是，一些不能通过"智能的优化在缓解的基本问题。  
  
## 概念  
 在对象生存期管理的一个要点是封装用户的对象不使用必须知道资源的对象拥有，或者如何释放它们，或者它是否拥有任何资源。  它必须只销毁对象。  C\+\+ 语言。核心构造反向顺序，即设计，确保对象销毁的正确时间块退出。  当销毁对象时，其基本和成员在特定订单被销毁。除非进行诸如新，堆分配或的位置的特定操作语言自动销毁对象。例如，[智能的指针](../cpp/smart-pointers-modern-cpp.md) 喜欢 `unique_ptr` 以及 `shared_ptr`和标准模板库 \(STL\) \(STL\) 容器，如 `vector`，该参数封装 `new`\/`delete` 和 `new[]`\/对象中`delete[]`，有析构函数。  因此使用的聪明指针、STL 容器很重要。  
  
 在生存期管理的另一个重要概念：析构函数。  析构函数封装资源的释放。\(常用的助记键是 RRID，资源的释放是销毁。\)资源是您从“System”获取并稍后必须归还的操作。内存是最常见的资源，但文件，还有、套接字、纹理和其他非内存资源。“拥有”resources 这意味着您可以使用，在需要时，还必须将其释放，则在您完成使用它。当销毁对象时，其析构函数释放它拥有的资源。  
  
 最终概念是 DAG \(处理的非循环性的图\)。所有权结构程序中的窗体 DAG。  对象不能自己本质上无意义的自身的不仅不可能，而且。  但是，这两个对象可以共享第三个对象的所有权。多个链接。可以在类似于 DAG:是的成员 B \(拥有 A，B\) C 上存有 `vector<D>` \(C\#\) 的每个电子 D 元素\)，存储 `shared_ptr<F>` \(共享所有权 E F，可以使用其他对象\)，依此类推。只要不周期，并且在 DAG 的每个链接由具有析构函数的对象表示形式 \(而非的原始指针、句柄或其他机制，\)，然后资源泄露是不可能的，因为阻止这些语言。  资源的释放，在不再需要它们后，垃圾回收器，没有运行。  生存期。跟踪堆栈大小、基本、Member 和相关参数是开销空闲，和可以小的 `shared_ptr`。  
  
### 基于堆的生存期  
 对于堆对象生存期，请使用 [智能的指针](../cpp/smart-pointers-modern-cpp.md)。  使用 `shared_ptr` 和 `make_shared` 作为默认指针和分布程序。  使用 `weak_ptr` 循环中断，执行缓存，并观察对象，不会影响或假定任何有关它们自己的生存期。  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 对于唯一所有权使用 `unique_ptr`，例如，在 *pimpl* 思路。（请参见[用于编译时封装的 Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)。）使 `unique_ptr` 的主要目标所有显式 `new` 表达式。  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 可以为非所有权和查看使用的原始指针。  非指针可能拥有的对，但是，它不会泄漏。  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 当需要时性能优化，可能需要使用 *封装* 自己指针和显式调用删除。  例如，在实现自己低数据结构时。  
  
### 基于堆栈的生存期  
 在现代 C\+\+，*基于堆栈的大小* 是一个强大的方法编写可靠的代码中，因为将自动 *堆栈生存期*，并使用最有效跟踪生存期的 *数据成员生存期* 实质上是自由开销。  尤其是在您处理的原始指针时，堆对象生存期要求工作手动管理，也可以是资源泄露和效率低下的问题源。  考虑此代码，演示基于堆栈的大小：  
  
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
  …  
  w.draw();  
  …  
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
  
```  
  
 慎重使用静态的生存期 \(全局静态函数，局部静态\)，因为问题可能出现。  当全局对象的构造函数引发异常，则发生什么情况？  通常，应用在出错难以调试的方法。  构造排序为静态的生存期对象是有问题的，并且不是并发安全的。  不仅对象构造问题，析构排序可能会很复杂，特别是多态性是包含在中的位置。  即使对象或变量不是多态的，并且不具有排序复杂性的构造\/销毁的，仍然存在线程安全并发问题。  一个多线程应用无法安全地修改在静态对象的数据不具有线程本地存储、锁定资源和其他特殊注意事项。  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)