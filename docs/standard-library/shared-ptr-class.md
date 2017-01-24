---
title: "shared_ptr 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "shared_ptr"
  - "tr1::shared_ptr"
  - "memory/std::tr1::shared_ptr"
  - "std::tr1::shared_ptr"
  - "std.tr1.shared_ptr"
  - "tr1.shared_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared_ptr 类"
  - "shared_ptr 类 [TR1]"
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
caps.latest.revision: 29
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shared_ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将引用计数智能指针回绕在动态分配的对象周围。  
  
## 语法  
  
```  
template<class Ty>  
   class shared_ptr {  
public:  
    typedef Ty element_type;  
  
    shared_ptr();  
    shared_ptr(nullptr_t);   
    shared_ptr(const shared_ptr& sp);  
    shared_ptr(shared_ptr&& sp);  
    template<class Other>  
        explicit shared_ptr(Other * ptr);  
    template<class Other, class D>  
        shared_ptr(Other * ptr, D dtor);  
    template<class D>  
        shared_ptr(nullptr_t, D dtor);  
    template<class Other, class D, class A>  
        shared_ptr(Other *ptr, D dtor, A alloc);  
    template<class D, class A>  
        shared_ptr(nullptr_t, D dtor, A alloc);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>&& sp);  
    template<class Other>  
        explicit shared_ptr(const weak_ptr<Other>& wp);  
    template<class Other>  
        shared_ptr(auto_ptr<Other>& ap);  
    template<class Other, class D>  
        shared_ptr(unique_ptr<Other, D>&& up);  
    template<class Other>  
        shared_ptr(const shared_ptr<Other>& sp, Ty *ptr);  
    ~shared_ptr();  
    shared_ptr& operator=(const shared_ptr& sp);  
    template<class Other>   
        shared_ptr& operator=(const shared_ptr<Other>& sp);  
    shared_ptr& operator=(shared_ptr&& sp);  
    template<class Other>   
        shared_ptr& operator=(shared_ptr<Other>&& sp);  
    template<class Other>   
        shared_ptr& operator=(auto_ptr< Other >&& ap);  
    template <class Other, class D>   
        shared_ptr& operator=(const unique_ptr< Other, D>& up) = delete;  
    template <class Other, class D>  
        shared_ptr& operator=(unique_ptr<Other, D>&& up);  
    void swap(shared_ptr& sp);  
    void reset();  
    template<class Other>  
        void reset(Other *ptr);  
    template<class Other, class D>  
        void reset(Other *ptr, D dtor);  
    template<class Other, class D, class A>  
        void reset(Other *ptr, D dtor, A alloc);  
    Ty *get() const;  
    Ty& operator*() const;  
    Ty *operator->() const;  
    long use_count() const;  
    bool unique() const;  
    operator bool() const;  
  
    template<class Other>  
        bool owner_before(shared_ptr<Other> const& ptr) const;  
    template<class Other>  
        bool owner_before(weak_ptr<Other> const& ptr) const;  
    template<class D, class Ty>   
        D* get_deleter(shared_ptr<Ty> const& ptr);  
};  
  
```  
  
#### 参数  
 `Ty`  
 由共享指针控制的类型。  
  
 `Other`  
 由参数指针控制的类型。  
  
 `ptr`  
 要复制的指针。  
  
 `D`  
 删除器的类型。  
  
 `A`  
 分配器的类型。  
  
 `dtor`  
 删除器。  
  
 `alloc`  
 分配器。  
  
 `sp`  
 要复制或移动的智能指针。  
  
 `wp`  
 要复制或移动的弱指针。  
  
 `ap`  
 要复制或移动的自动指针。  
  
 `up`  
 要移动的唯一指针。  
  
## 备注  
 模板类描述使用引用计数来管理资源的对象。  `shared_ptr` 对象有效保留一个指向其拥有的资源的指针或保留一个 null 指针。  资源可由多个 `shared_ptr` 对象拥有；当拥有特定资源的最后一个 `shared_ptr` 对象被销毁后，资源将释放。  
  
 在重新分配或重置资源后，`shared_ptr` 将停止拥有该资源。  
  
 模板参数 `Ty` 可能是一个不完整的类型，针对某些成员函数的情况除外。  
  
 当从类型 `shared_ptr<Ty>` 的资源指针或 `G*` 中构造 `shared_ptr<G>` 对象时，指针类型 `G*` 必须可转换为 `Ty*`。  如果不是这样，则代码将不进行编译。  例如:  
  
```cpp  
class F {};  
class G : public F {};  
```  
  
```cpp  
  
#include <memory>  
  
using namespace std;  
  
shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*  
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>  
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*  
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>  
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>  
shared_ptr<int> sp5(new G); // error, G* not convertible to int*  
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>  
```  
  
 一个 `shared_ptr` 对象拥有一个资源：  
  
-   如果已使用指向该资源的指针构造它，  
  
-   如果已从拥有该资源的 `shared_ptr` 对象构造它，  
  
-   如果已从指向该资源的 [weak\_ptr 类](../standard-library/weak-ptr-class.md) 对象构造它，或  
  
-   如果已使用 [shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md) 或通过调用成员函数 [shared\_ptr::reset](../Topic/shared_ptr::reset.md) 将该资源的所有权分配给它。  
  
 拥有资源的 `shared_ptr` 对象共享控制块。  控制块包含：  
  
-   拥有该资源的 `shared_ptr` 对象的数目，  
  
-   指向该资源的 `weak_ptr` 对象的数目；  
  
-   该资源的删除器（如果有），  
  
-   控制块的自定义分配器（如果有）。  
  
 使用 null 指针初始化的 `shared_ptr` 对象具有控制块且不为空。  在 `shared_ptr` 对象释放资源之后，它将不再拥有该资源。  在 `weak_ptr` 对象释放资源之后，它将不再指向该资源。  
  
 当拥有资源的 `shared_ptr` 对象的数目变为零时，可通过删除该资源或将其地址传递给删除器来释放资源，这取决于最初创建资源所有权的方式。  当拥有资源的 `shared_ptr` 对象的数目数为零，并且指向该资源的 `weak_ptr` 对象的数目为零时，可使用控制块的自定义分配器（如果有）来释放控制块。  
  
 空 `shared_ptr` 对象不拥有任何资源和控制块。  
  
 删除器是一个拥有成员函数 `operator()` 的函数对象。  其类型必须是可复制构造的，而且其副本构造函数和析构函数不得引发异常。  它接受一个参数（即要删除的对象）。  
  
 一些函数具有一个参数列表，此列表定义了生成的 `shared_ptr<Ty>` 或 `weak_ptr<Ty>` 对象的属性。  您可通过多种方法指定此类参数列表：  
  
 无参数 \- 生成的对象是一个空 `shared_ptr` 对象或者一个空 `weak_ptr` 对象。  
  
 `ptr` \-\- 一个指向要管理的资源的类型 `Other*` 的指针。  `Ty` 必须是完整类型。  如果函数失败（因为无法分配控制块），则将计算表达式 `delete ptr` 的结果。  
  
 `ptr, dtor` \- 一个指向要管理的资源的类型 `Other*` 的指针和一个针对该资源的删除器。  如果函数失败（因为无法分配控制块），则调用必须经过良好定义的 `dtor(ptr)`。  
  
 `ptr, dtor, alloc` \- 一个指向要管理的资源的类型 `Other*` 的指针、一个针对资源的删除器和一个用于管理必须分配和释放的任何存储的分配器。  如果函数失败（因为无法分配控制块），则调用必须经过良好定义的 `dtor(ptr)`。  
  
 `sp` \- 一个拥有要管理的资源的 `shared_ptr<Other>` 对象。  
  
 `wp` \- 一个指向要管理的资源的 `weak_ptr<Other>` 对象。  
  
 `ap` \- 一个拥有指向要管理的资源的指针的 `auto_ptr<Other>` 对象。  如果函数成功，则调用 `ap.release()`；否则保持 `ap` 不变。  
  
 在所有情况下，指针类型 `Other*` 必须可转换为 `Ty*`。  
  
## 线程安全  
 多个线程可以同时读取和写入不同的 `shared_ptr` 对象，即使这些对象是共享所有权的副本。  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[shared\_ptr::shared\_ptr](../Topic/shared_ptr::shared_ptr.md)|构造一个 `shared_ptr`。|  
|[shared\_ptr::~shared\_ptr](../Topic/shared_ptr::~shared_ptr.md)|销毁 `shared_ptr`。|  
  
### 方法  
  
|||  
|-|-|  
|[shared\_ptr::element\_type](../Topic/shared_ptr::element_type.md)|元素的类型。|  
|[shared\_ptr::get](../Topic/shared_ptr::get.md)|获取拥有的资源的地址。|  
|[shared\_ptr::owner\_before](../Topic/shared_ptr::owner_before.md)|如果此 `shared_ptr` 排在提供的指针之前（或小于该指针），则返回 true。|  
|[shared\_ptr::reset](../Topic/shared_ptr::reset.md)|替换拥有的资源。|  
|[shared\_ptr::swap](../Topic/shared_ptr::swap.md)|交换两个 `shared_ptr` 对象。|  
|[shared\_ptr::unique](../Topic/shared_ptr::unique.md)|测试拥有的资源是否是唯一的。|  
|[shared\_ptr::use\_count](../Topic/shared_ptr::use_count.md)|计算资源所有者的数目。|  
  
### 运算符  
  
|||  
|-|-|  
|[shared\_ptr::operator boolean\-type](../Topic/shared_ptr::operator%20boolean-type.md)|测试拥有的资源是否存在。|  
|[shared\_ptr::operator\*](../Topic/shared_ptr::operator*.md)|获取指定的值。|  
|[shared\_ptr::operator\=](../Topic/shared_ptr::operator=.md)|替换拥有的资源。|  
|[shared\_ptr::operator\-\>](../Topic/shared_ptr::operator-%3E.md)|获取指向指定的值的指针。|  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [weak\_ptr 类](../standard-library/weak-ptr-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)