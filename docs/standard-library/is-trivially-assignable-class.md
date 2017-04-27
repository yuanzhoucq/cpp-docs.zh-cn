---
title: "is_trivially_assignable 类 | Microsoft Docs"
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
- is_trivially_assignable
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4b640307631b1407e5309adaa63b39e100839f91
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable 类
测试 `From` 类型的值是否能够普通赋予 `To` 类型  
  
## <a name="syntax"></a>语法  
  
```
template <class To, class From>  
struct is_trivially_assignable;
```  
  
#### <a name="parameters"></a>参数  
 到  
 接收赋值的对象的类型。  
  
 从  
 提供值的对象的类型。  
  
## <a name="remarks"></a>备注  
 表达式 `declval<To>() = declval<From>()` 必须格式正确，且编译器必须已知其不需要任何重要操作。 `From` 和 `To` 都必须是完整类型、`void` 或具有未知边界的数组。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




