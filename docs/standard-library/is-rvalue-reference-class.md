---
title: "is_rvalue_reference 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_rvalue_reference
- std::is_rvalue_reference
- type_traits/std::is_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
caps.latest.revision: 16
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
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 748a717c1f49206457bded1cd11be2dd30753f6f
ms.lasthandoff: 02/24/2017

---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 类
测试类型是否是右值引用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_rvalue_reference;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)，则此类型谓词的实例为 true。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)




