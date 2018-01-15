---
title: "is_nothrow_copy_assignable 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_copy_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fe17d40b104c1ae06ac8158db79925c0731d3ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 类
测试类型是否具有编译器已知不会引发的复制赋值运算符。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
struct is_nothrow_copy_assignable;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果可引用类型 `T` 的 `is_nothrow_assignable<T&, const T&>` 为 true，则类型谓词的实例为 true；否则为 false。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [is_nothrow_assignable 类](../standard-library/is-nothrow-assignable-class.md)   





