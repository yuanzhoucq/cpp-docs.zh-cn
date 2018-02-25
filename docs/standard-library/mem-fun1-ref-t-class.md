---
title: "mem_fun1_ref_t 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun1_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35dd25e56ba838864eeeb64d43fc8c2d25cff803
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t 类
一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将仅带一个自变量的 **non_const** 成员函数作为二元函数对象调用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>参数  
 `_Pm`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
 `left`  
 要在其上调用 `_Pm` 成员函数的对象。  
  
 `right`  
 为 `_Pm` 提供的自变量。  
  
## <a name="return-value"></a>返回值  
 一个自适应二元函数。  
  
## <a name="remarks"></a>备注  
 模板类存储 `_Pm` 的副本，它必须是专用成员对象中指向类 **Type** 的成员函数的指针。 它定义其成员函数`operator()`为返回 (**左**。\*`_Pm`) (**右**)。  
  
## <a name="example"></a>示例  
 通常不直接使用 `mem_fun1_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



