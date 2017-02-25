---
title: "reference_wrapper 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.reference_wrapper"
  - "tr1.reference_wrapper"
  - "reference_wrapper"
  - "tr1::reference_wrapper"
  - "xrefwrap/std::tr1::reference_wrapper"
  - "std::tr1::reference_wrapper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference_wrapper 类"
  - "reference_wrapper 类 [TR1]"
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# reference_wrapper 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装引用。  
  
## 语法  
  
```  
template<class Ty>  
    class reference_wrapper  
    : public unary_function<T1, Ret>        // see below  
    : public binary_function<T1, T2, Ret>   // see below  
    {  
public:  
    typedef Ty type;  
    typedef T0 result_type;                 // see below  
  
    reference_wrapper(Ty&);  
  
    Ty& get() const;  
    operator Ty&() const;  
    template<class T1, class T2, ..., class TN>  
        typename result_of<T(T1, T2, ..., TN)>::type  
        operator()(T1&, T2&, ..., TN&);  
  
private:  
    Ty *ptr; // exposition only  
    };  
```  
  
## 备注  
 `reference_wrapper<Ty>` 是可构造且可赋值的副本，并保留指向 `Ty` 类型对象的指针。  
  
 仅当类型 `Ty` 为以下类型时，专用化 `reference_wrapper<Ty>` 才派生自 `std::unary_function<T1, Ret>`（因此将嵌套类型 `result_type` 定义为 `Ret` 的同义词，将嵌套类型 `argument_type` 定义为 `T1` 的同义词）：  
  
 函数类型或指向函数类型（采用一个 `T1` 类型的参数并返回 `Ret`）的指针；或  
  
 指向成员函数 `Ret T::f() cv` 的指针，其中 `cv` 表示成员函数的 cv\- 限定符；类型 `T1` 为 `cv` `T*`；或  
  
 派生自 `unary_function<T1, Ret>` 的类类型。  
  
 仅当类型 `Ty` 为以下类型时，专用化 `reference_wrapper<Ty>` 才派生自 `std::binary_function<T1, T2, Ret>`（因此将嵌套类型 `result_type` 定义为 `Ret` 的同义词，将嵌套类型 `first_argument_type` 定义为 `T1` 的同义词以及将嵌套类型 `second_argument_type` 定义为 `T2` 的同义词）：  
  
 函数类型或指向函数类型（采用两个 `T1` 类型和 `T2` 类型的参数并返回 `Ret`）的指针；或  
  
 指向成员函数 `Ret T::f(T2) cv` 的指针，其中 `cv` 表示成员函数的 cv\- 限定符；类型 `T1` 为 `cv` `T*`；或  
  
 派生自 `binary_function<T1, T2, Ret>` 的类类型。  
  
### 构造函数  
  
|||  
|-|-|  
|[reference\_wrapper::reference\_wrapper](../Topic/reference_wrapper::reference_wrapper.md)|构造一个 `reference_wrapper`。|  
  
### Typedef  
  
|||  
|-|-|  
|[reference\_wrapper::result\_type](../Topic/reference_wrapper::result_type.md)|已包装引用的弱结果类型。|  
|[reference\_wrapper::type](../Topic/reference_wrapper::type.md)|已包装引用的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[reference\_wrapper::get](../Topic/reference_wrapper::get.md)|获取已包装的引用。|  
  
### 运算符  
  
|||  
|-|-|  
|[reference\_wrapper::operator Ty&](../Topic/reference_wrapper::operator%20Ty&.md)|获取指向已包装引用的指针。|  
|[reference\_wrapper::operator\(\)](../Topic/reference_wrapper::operator\(\).md)|调用已包装的引用。|  
  
## 要求  
 **标头：**\<functional\>  
  
 **命名空间:** std  
  
## 请参阅  
 [cref 函数](../Topic/cref%20Function.md)   
 [ref 函数](../Topic/ref%20Function.md)