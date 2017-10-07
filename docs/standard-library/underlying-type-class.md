---
title: "underlying_type 类 | Microsoft Docs"
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
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 8d5af1b1115d2845fcfa4dbd89dc3776e7e66ccf
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="underlyingtype-class"></a>underlying_type 类
生成枚举类型的基础整型类型。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
struct underlying_type;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要修改的类型。  
  
## <a name="remarks"></a>备注  
 如果 `T` 是一个枚举类型，则模板类的 `type` 成员 typedef 将为 `T` 的基础整型类型命名，否则没有任何成员 typedef `type`。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




