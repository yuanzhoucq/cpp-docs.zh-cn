---
title: "is_nothrow_constructible 类 | Microsoft Docs"
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
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 2ff20de3656cde44d79936c6bf1374134eb95068
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible 类
测试类型是否可构造以及是否已知该类型在使用指定参数类型时不会引发。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, class... Args>  
struct is_nothrow_constructible;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要查询的类型。  
  
 `Args`  
 `T` 的构造函数中要匹配参数类型。  
  
## <a name="remarks"></a>备注  
 如果通过使用 `Args` 中的参数类型可构造类型 `T`，且编译器已知该构造函数不会引发，则类型谓词的实例为 true；否则为 false。 如果变量定义 `T t(std::declval<Args>()...);` 的格式正确，则可构造类型 `T`。 `T` 和 `Args` 中的所有类型都必须是完整类型、`void` 或具有未知边界的数组。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




