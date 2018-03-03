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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02698c90714ae530e827d9bfbe6cdc7ce1fd0abf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)



