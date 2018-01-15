---
title: "alignment_of 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::alignment_of
dev_langs: C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de94e34dd0e00a2902454b4ab41f1790c194b6dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="alignmentof-class"></a>alignment_of 类
获取指定类型的对齐方式。 此结构根据 [alignof](../cpp/alignof-and-alignas-cpp.md) 来实现。 只需查询对齐方式值时可直接使用 `alignof`。 需要整数常量时（例如在执行标记调度时），可使用 alignment_of。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct alignment_of;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 类型查询可保存 `Ty` 类型的对齐方式的值。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [aligned_storage 类](../standard-library/aligned-storage-class.md)
