---
title: "result_of 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- result_of
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- result_of
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 8ffd540b812aedcc3cff9703a1b45ef2ce57983c
ms.lasthandoff: 02/24/2017

---
# <a name="resultof-class"></a>result_of 类
确定可调用类型的返回类型，该可调用类型采用指定参数类型。  
  
## <a name="syntax"></a>语法  
  
```  
template<class>  
struct result_of; // Causes a static assert  
  
template <class Fn, class... ArgTypes>  
struct result_of<Fn(ArgTypes...)>;

// Helper type  
template<class T>
   using result_of_t = typename result_of<T>::type;
```  
  
#### <a name="parameters"></a>参数  
 `Fn`  
 要查询的可调用类型。  
  
 `ArgTypes`  
 供可调用类型查询的参数列表的类型。  
  
## <a name="remarks"></a>备注  
 使用此模板可在编译时确定 `Fn`(`ArgTypes`) 的结果类型，其中 `Fn` 是可调用类型、对函数的引用或对可调用类型的引用（通过在 `ArgTypes` 中使用类型的参数列表进行调用）。 如果未计算的表达式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正确，则模板类的 `type` 成员为 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的结果类型命名。 否则，此模板类不具有任何成员 `type`。 类型 `Fn` 和参数包 `ArgTypes` 中的所有类型必须是完整的类型、`void` 或未知边界数组。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




