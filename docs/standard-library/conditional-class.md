---
title: "conditional 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 2c764bfc42d633a3036f2e567078b9ea39feea8b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="conditional-class"></a>conditional 类
根据指定的条件，从两种类型之中选择其中一种。  
  
## <a name="syntax"></a>语法  
  
```
template <bool B, class T1, class T2>  
struct conditional;

template <bool _Test, class _T1, class _T2>  
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```  
  
#### <a name="parameters"></a>参数  
 `B`  
 用于确定所选类型的值。  
  
 `T1`  
 当 B 为 true 时的类型结果。  
  
 `T2`  
 当 B 为 false 时的类型结果。  
  
## <a name="remarks"></a>备注  
 当 `conditional<B, T1, T2>::type` 的计算结果为 `T1` 时，模板成员 typedef `B` 的计算结果为 `true`，当 `T2` 的计算结果为 `B` ，其计算结果为 `false`。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




