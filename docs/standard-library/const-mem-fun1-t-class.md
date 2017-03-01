---
title: "const_mem_fun1_t 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.const_mem_fun1_t
- xfunctional/std::const_mem_fun1_t
- std::const_mem_fun1_t
- const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 3a2664541cd1f1a44988f81e227e553b75b4faa6
ms.lasthandoff: 02/24/2017

---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 类
一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 **const** 成员函数作为二元函数对象调用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>  
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>参数  
 `_Pm`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
 `_Pleft`  
 要在其上调用 `_Pm` 成员函数的 **const** 对象。  
  
 `right`  
 为 `_Pm` 提供的自变量。  
  
## <a name="return-value"></a>返回值  
 一个自适应二元函数。  
  
## <a name="remarks"></a>备注  
 模板类存储 `_Pm` 的副本，它必须是专用成员对象中指向类 **Type** 的成员函数的指针。 它将其成员函数 `operator()` 定义为返回 ( **_Pleft**->\* *Pm)(***Right**) **const**。  
  
## <a name="example"></a>示例  
 通常不直接使用 `const_mem_fun1_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun_function)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




