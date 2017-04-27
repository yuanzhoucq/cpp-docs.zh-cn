---
title: "is_lvalue_reference 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_lvalue_reference
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: 18
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 71a98284e641ad5d24dc3f1413bdf8d210b2091a
ms.lasthandoff: 02/24/2017

---
# <a name="islvaluereference-class"></a>is_lvalue_reference 类
测试类型是否是左值引用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_lvalue_reference;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是对某个对象或函数的引用，此类型谓词的实例将为 true，否则为 false。 请注意，`Ty` 可能不是右值引用。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)




