---
title: "mem_fun_ref_t 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xfunctional/std::mem_fun_ref_t
- mem_fun_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
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
ms.openlocfilehash: a462fa28f086f2ff0f74e35594dbd651e6d416d9
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="memfunreft-class"></a>mem_fun_ref_t 类
一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将不带任何自变量的 **non_const** 成员函数作为一元函数对象调用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;

 };
```  
  
#### <a name="parameters"></a>参数  
 `_Pm`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
 `left`  
 要在其上调用 `_Pm` 成员函数的对象。  
  
## <a name="return-value"></a>返回值  
 一个自适应一元函数。  
  
## <a name="remarks"></a>备注  
 此模板类将 `_Pm` 的副本存储于私有成员对象中，该副本必须为指向 **Type** 类的成员函数的指针。 它将其成员函数 `operator()` 定义为返回 ( **left**.* `_Pm`)( )。  
  
## <a name="example"></a>示例  
  通常不直接使用 `mem_fun_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




