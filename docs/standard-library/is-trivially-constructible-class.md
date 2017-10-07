---
title: "is_trivially_constructible 类 | Microsoft Docs"
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
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 109e119100a3cb561159cca9bce95f793922e58d
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible 类
测试使用指定参数类型时类型是否为普通构造类型。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class... Args>  
struct is_trivially_constructible;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要查询的类型。  
  
 `Args`  
 `T` 的构造函数中要匹配参数类型。  
  
## <a name="remarks"></a>备注  
 如果通过使用 `Args` 中的参数类型可普通构造类型 `T`，则类型谓词的实例为 true；否则为 false。 如果变量定义 `T t(std::declval<Args>()...);` 格式正确且已知其不会调用任何重要的操作，则类型 `T` 为普通构造类型。 `T` 和 `Args` 中的所有类型都必须是完整类型、`void` 或具有未知边界的数组。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




