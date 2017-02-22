---
title: "weak_ptr 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.weak_ptr"
  - "tr1.weak_ptr"
  - "weak_ptr"
  - "tr1::weak_ptr"
  - "std::tr1::weak_ptr"
  - "memory/std::tr1::weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "weak_ptr 类"
  - "weak_ptr 类 [TR1]"
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# weak_ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

回绕弱链接指针。  
  
## 语法  
  
```  
template<class Ty> class weak_ptr {  
public:  
    typedef Ty element_type;  
  
    weak_ptr();  
    weak_ptr(const weak_ptr&);  
    template<class Other>  
        weak_ptr(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr(const shared_ptr<Other>&);  
  
    weak_ptr& operator=(const weak_ptr&);  
    template<class Other>  
        weak_ptr& operator=(const weak_ptr<Other>&);  
    template<class Other>  
        weak_ptr& operator=(shared_ptr<Other>&);  
  
    void swap(weak_ptr&);  
    void reset();  
  
    long use_count() const;  
    bool expired() const;  
    shared_ptr<Ty> lock() const;  
    };  
```  
  
#### 参数  
 `Ty`  
 由弱指针控制的类型。  
  
## 备注  
 此模板类描述了一个指向由一个或多个 [shared\_ptr 类](../standard-library/shared-ptr-class.md) 对象管理的资源的对象。  指向某个资源的 `weak_ptr` 对象不会影响资源的引用计数。  因此，当最后一个管理该资源 `shared_ptr` 的对象被销毁时，则即使存在指向该资源的 `weak_ptr` 对象，该资源也将被释放。  这对于避免数据结构中的循环至关重要。  
  
 在以下情况下 `weak_ptr` 对象将指向某个资源：如果该对象是从拥有该资源的 `shared_ptr` 对象构造而成、如果是从指向该资源的 `weak_ptr` 对象构造而成、或者使用 [weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md) 将该资源分配到了该对象。  `weak_ptr` 对象不提供直接访问其所指向的资源的权限。  需要使用该资源的代码可通过一个 `shared_ptr` 对象来执行该操作，该对象通过调用成员函数 [weak\_ptr::lock](../Topic/weak_ptr::lock.md) 创建并拥有该资源。  `weak_ptr` 对象在其所指向的资源被释放时已过期，因为所有拥有该资源的 `shared_ptr` 对象已被销毁。  调用已过期的 `weak_ptr` 对象上的 `lock` 将创建一个空 shared\_ptr 对象。  
  
 空 weak\_ptr 对象不会指向任何资源，而且没有控制块。  其成员函数 `lock` 将返回一个空 shared\_ptr 对象。  
  
 当两个或多个由 `shared_ptr` 对象控制的资源保留有相互引用的 `shared_ptr` 对象时，会发生循环。  例如，具有三个元素的循环的链接列表有一个头节点 `N0`；该节点保留有一个拥有下一个节点 `N1` 的 `shared_ptr` 对象；该节点保留有一个拥有下一个节点 `N2` 的 `shared_ptr` 对象；反过来，该节点保留有一个拥有头节点 `N0` 的 `shared_ptr` 对象，由此形成闭合循环。  在此情况下，没有引用计数将变为零，并且不会释放循环中的节点。  若要消除循环，最后一个节点 `N2` 应保留指向 `N0` 的 `weak_ptr` 对象，而不是 `shared_ptr` 对象。  由于 `weak_ptr` 对象不拥有 `N0`，因此不会影响 `N0` 的引用计数，并且销毁该程序对头节点的最后一个引用时，也将销毁列表中的节点。  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[weak\_ptr::weak\_ptr](../Topic/weak_ptr::weak_ptr.md)|构造一个 `weak_ptr`。|  
  
### 方法  
  
|||  
|-|-|  
|[weak\_ptr::element\_type](../Topic/weak_ptr::element_type.md)|元素的类型。|  
|[weak\_ptr::expired](../Topic/weak_ptr::expired.md)|测试所属权是否已过期。|  
|[weak\_ptr::lock](../Topic/weak_ptr::lock.md)|获取资源的独占所属权。|  
|[weak\_ptr::owner\_before](../Topic/weak_ptr::owner_before.md)|如果此 `weak_ptr` 排在提供的指针之前（或小于该指针），则返回 `true`。|  
|[weak\_ptr::reset](../Topic/weak_ptr::reset.md)|释放所拥有的资源。|  
|[weak\_ptr::swap](../Topic/weak_ptr::swap.md)|交换两个 `weak_ptr` 对象。|  
|[weak\_ptr::use\_count](../Topic/weak_ptr::use_count.md)|指定 `shared_ptr` 对象的计数。|  
  
### 运算符  
  
|||  
|-|-|  
|[weak\_ptr::operator\=](../Topic/weak_ptr::operator=.md)|替换所拥有的资源。|  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [shared\_ptr 类](../standard-library/shared-ptr-class.md)