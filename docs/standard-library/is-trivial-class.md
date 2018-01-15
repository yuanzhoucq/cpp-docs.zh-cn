---
title: "is_trivial 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivial
dev_langs: C++
helpviewer_keywords: is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccf641e5f5e2bd3a224b418666882fa022289cfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="istrivial-class"></a>is_trivial 类
测试类型是否为通常类型。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
struct is_trivial;
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `T` 是常用类型，则类型谓词的实例为 true；否则为 false。 常用类型是标量类型、完全可复制类类型、这些类型的数组以及这些类型的 cv 限定版本。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)



