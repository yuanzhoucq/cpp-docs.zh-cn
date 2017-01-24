---
title: "function 类 | Microsoft Docs"
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
  - "functional/std::tr1::function"
  - "std.tr1.function"
  - "std::tr1::function"
  - "function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "function 类 [TR1]"
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
caps.latest.revision: 26
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# function 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可调用对象的包装。  
  
## 语法  
  
```cpp  
template<class Fty>  
   class function  // Fty of type Ret(T1, T2, ..., TN)  
   : public unary_function<T1, Ret>       // when Fty is Ret(T1)  
   : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)  
   {  
public:  
   typedef Ret result_type;  
  
   function();  
   function(nullptr_t);  
   function(const function& _Right);  
   template<class Fty2>  
      function(Fty2 fn);  
   template<class Fty2, class Alloc>  
       function (reference_wrapper<Fty2>, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       void assign (Fty2, const Alloc& _Ax);  
   template<class Fty2, class Alloc>  
       assign (reference_wrapper<Fty2>, const Alloc& _Ax);  
```  
  
```cpp  
function& operator=(nullptr_t);  
function& operator=(const function&);  
template<class Fty2>  
   function& operator=(Fty2);  
template<class Fty2>  
   function& operator=(reference_wrapper<Fty2>);  
void swap(function&);  
  
explicit operator bool() const;  
result_type operator()(T1, T2, ....., TN) const;  
  
const std::type_info& target_type() const;  
template<class Fty2>  
   Fty2 *target();  
template<class Fty2>  
   const Fty2 *target() const;  
```  
  
```cpp  
   template<class Fty2>  
      void operator==(const Fty2&) const = delete;  
   template<class Fty2>  
      void operator!=(const Fty2&) const = delete;  
};  
```  
  
#### 参数  
 `Fty`  
 封装函数类型。  
  
 `_Ax`  
 分配程序函数。  
  
## 备注  
 模板类是调用签名是 `Ret(T1, T2, ..., TN)`的包装调用。  可以在一种统一使用包装它包含多种可调用对象。  
  
 某些成员函数采用所需目标命名对象的操作数。  可以采用多种方式指定此操作数：  
  
 `fn` \-\-可调用对象；`fn`在调用 `function` 对象容纳 `fn`后复制  
  
 `fnref` \-\- `fnref.get()`命名可调用对象；在调用 `function` 对象对 `fnref.get()`的引用后  
  
 `right` \-\-可调用对象，如果存在，使 `function` 对象的 `right`。  
  
 `npc` \-\-空指针；调用后 `function` 对象为空  
  
 在任何情况下，`INVOKE(f, t1, t2, ..., tN)`，`f` 是可调用的对象，`t1, t2, ..., tN` 分别为类型 `T1, T2, ..., TN` lvalue，必须是格式良好，如果 `Ret` 不是无效，转换为 `Ret`。  
  
 一个空 `function` 对象持有可调用对象或引用到可调用对象。  
  
### 构造函数  
  
|||  
|-|-|  
|[function::function](../Topic/function::function.md)|构造包装为空或存储任意类型可调用对象具有固定的签名。|  
  
### Typedef  
  
|||  
|-|-|  
|[function::result\_type](../Topic/function::result_type.md)|存储可调用对象的返回类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[function::assign](../Topic/function::assign.md)|指派给此对象的函数可调用对象。|  
|[function::swap](../Topic/function::swap.md)|交换两个可调用对象。|  
|[function::target](../Topic/function::target.md)|测试，如果存储可调用对象是可调用的。指定。|  
|[function::target\_type](../Topic/function::target_type.md)|获得有关可调用对象的类型信息。|  
  
### 运算符  
  
|||  
|-|-|  
|[function::operator 未指定](../Topic/function::operator%20unspecified.md)|测试，如果存储可调用对象存在。|  
|[function::operator\(\)](../Topic/function::operator\(\).md)|调用可调用对象。|  
|[function::operator\=](../Topic/function::operator=.md)|替换存储可调用对象。|  
  
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [mem\_fn 函数](../Topic/mem_fn%20Function.md)   
 [reference\_wrapper 类](../standard-library/reference-wrapper-class.md)