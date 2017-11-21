---
title: "CompareStringOrdinal 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs: C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17415efa6519d8e3538f869168db2040ed6e73dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>参数  
 `lhs`  
 要比较的第一个 HSTRING。  
  
 `rhs`  
 要比较的第二个 HSTRING。  
  
## <a name="return-value"></a>返回值  
  
|值|条件|  
|-----------|---------------|  
|-1|`lhs` 小于 `rhs`。|  
|0|`lhs` 等于 `rhs`。|  
|1|`lhs` 大于 `rhs`。|  
  
## <a name="remarks"></a>备注  
 比较两个指定的 HSTRING 对象并返回一个整数，指示二者在排序顺序中的相对位置。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)