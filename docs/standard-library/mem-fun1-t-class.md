---
title: "mem_fun1_t 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mem_fun1_t
- xfunctional/std::mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 6f9335afb06b8d07f96dc3d0fc320016a0aad7ab
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="memfun1t-class"></a>mem_fun1_t 类
一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 **non_const** 成员函数作为二元函数对象调用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>参数  
 `_Pm`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
 `_Pleft`  
 要在其上调用 `_Pm` 成员函数的对象。  
  
 `right`  
 为 `_Pm` 提供的自变量。  
  
## <a name="return-value"></a>返回值  
 一个自适应二元函数。  
  
## <a name="remarks"></a>备注  
 此模板类将 `_Pm` 的副本存储于私有成员对象中，该副本必须为指向 **Type** 类的成员函数的指针。 它定义其成员函数 `operator()` 为返回 ( **_Pleft**->\* `_Pm`)( **right**)。  
  
## <a name="example"></a>示例  
  通常不直接使用 `mem_fun1_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




