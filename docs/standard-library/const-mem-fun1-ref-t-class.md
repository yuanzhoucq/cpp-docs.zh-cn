---
title: "const_mem_fun1_ref_t 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun1_ref_t
dev_langs: C++
helpviewer_keywords: const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 935584fd4033bfaadc0b47a1ddad15d1d20f6b6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t 类
一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将仅带一个自变量的 **const** 成员函数作为二元函数对象调用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
 : public binary_function<Type, Arg, Result> 
 {
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>参数  
 `Pm`  
 一个指针，指向要转换为函数对象的 **Type** 类成员函数。  
  
 `left`  
 要在其上调用 `Pm` 成员函数的 **const** 对象。  
  
 `right`  
 为 `Pm` 提供的自变量。  
  
## <a name="return-value"></a>返回值  
 一个自适应二元函数。  
  
## <a name="remarks"></a>备注  
 模板类存储 `Pm` 的副本，它必须是专用成员对象中指向类 **Type** 的成员函数的指针。 它将其成员函数 `operator()` 定义为返回 ( `left`.\**Pm*)( `right`) **const**。  
  
## <a name="example"></a>示例  
 通常不直接使用 `const_mem_fun1_ref_t` 的构造函数；helper 函数 `mem_fun_ref` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



