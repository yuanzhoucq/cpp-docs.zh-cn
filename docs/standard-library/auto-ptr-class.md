---
title: "auto_ptr 类 | Microsoft Docs"
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
  - "std::auto_ptr"
  - "std.auto_ptr"
  - "auto_ptr"
  - "memory/std::auto_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_ptr 类"
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
caps.latest.revision: 26
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# auto_ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在资源周围包装智能指针，确保在块失去控制权时自动销毁该资源。  
  
 功能更强大的 `unique_ptr` 类可取代 `auto_ptr`。  有关详细信息，请参阅 [unique\_ptr 类](../standard-library/unique-ptr-class.md)。  
  
 有关 `throw()` 和异常处理的详细信息，请参阅[异常规范 \(throw\)](../cpp/exception-specifications-throw-cpp.md)。  
  
## 语法  
  
```  
template<class Type>  
    class auto_ptr {  
public:  
    typedef Type element_type;  
    explicit auto_ptr(Type *_Ptr = 0) throw();  
    auto_ptr(auto_ptr<Type>& _Right) throw();  
    template<class Other>  
        operator auto_ptr<Other>() throw();  
    template<class Other>  
        auto_ptr<Type>& operator=(auto_ptr<Other>& _Right) throw();  
    template<class Other>  
        auto_ptr(auto_ptr<Other>& _Right);  
    auto_ptr<Type>& operator=(auto_ptr<Type>& _Right);  
    ~auto_ptr();  
    Type& operator*() const throw();  
    Type *operator->()const throw();  
    Type *get() const throw();  
    Type *release()throw();  
    void reset(Type *_Ptr = 0);  
};  
```  
  
#### 参数  
 `_Right`  
 可从中获取现有资源的 `auto_ptr`。  
  
 `_Ptr`  
 指定用于替换已存储指针的指针。  
  
## 备注  
 此模板类描述指向已分配对象的智能指针（名为 `auto_ptr,`）。  指针必须为 Null 或指定 `new` 所分配的对象。  如果 `auto_ptr` 的存储值已分配给其他对象，则它将转移所有权。  （它在与 Null 指针进行转移后替换存储值。） `auto_ptr<Type>` 的析构函数将删除已分配的对象。  `auto_ptr<Type>` 可确保在块失去控制权时（甚至在已引发异常的情况下）自动删除已分配的对象。  不应构造两个拥有相同对象的 `auto_ptr<Type>` 对象。  
  
 可以将 `auto_ptr<Type>` 对象作为函数调用的参数按值传递。  `auto_ptr` 不能是任何标准库容器的元素。  无法使用标准模板库容器可靠地管理一系列 `auto_ptr<Type>` 对象。  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[auto\_ptr](../Topic/auto_ptr::auto_ptr.md)|`auto_ptr` 类型的对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[element\_type](../Topic/auto_ptr::element_type.md)|类型是模板参数 `Type` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[get](../Topic/auto_ptr::get.md)|该成员函数将返回存储的指针 `myptr`。|  
|[发布](../Topic/auto_ptr::release.md)|该成员将存储的指针 `myptr` 替换为 Null 指针，并返回以前存储的指针。|  
|[重置](../Topic/auto_ptr::reset.md)|此成员函数对表达式 `delete myptr` 进行求值，但仅在存储的指针值 `myptr` 因函数调用而更改时进行。  然后它将存储的指针替换为 `ptr`。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/auto_ptr::operator=.md)|一个赋值运算符，用于将所有权从一个 `auto_ptr` 对象转移到到其他对象。|  
|[operator\*](../Topic/auto_ptr::operator*.md)|`auto_ptr` 类型的对象的取消引用运算符。|  
|[operator\-\>](../Topic/auto_ptr::operator-%3E.md)|允许成员访问的运算符。|  
|[运算符 auto\_ptr\<Other\>](../Topic/auto_ptr::operator%20auto_ptr%3COther%3E.md)|将某种 `auto_ptr` 强制转换为另一种 `auto_ptr`。|  
|[运算符 auto\_ptr\_ref\<Other\>](../Topic/auto_ptr::operator%20auto_ptr_ref%3COther%3E.md)|将 `auto_ptr` 强制转换为 `auto_ptr_ref`。|  
  
## 要求  
 **标头：** \<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [unique\_ptr 类](../standard-library/unique-ptr-class.md)