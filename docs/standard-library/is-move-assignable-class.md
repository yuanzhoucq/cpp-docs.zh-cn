---
title: "is_move_assignable 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_move_assignable
dev_langs: C++
helpviewer_keywords: is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1db589d15042a5e94223aa0f711f58cb30da9983
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ismoveassignable-class"></a>is_move_assignable 类
测试类型是否可移动赋值。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
struct is_move_assignable;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型的右值引用可赋予此类型的引用，则该类型可移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 可移动赋值的类型包括可引用的标量类型和类类型，这些类型具有编译器生成的移动赋值运算符或用户定义的移动赋值运算符。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)



