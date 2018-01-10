---
title: "conditional 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::conditional
dev_langs: C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a106f2361dccbeb33c662c88edd40223a604639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)



