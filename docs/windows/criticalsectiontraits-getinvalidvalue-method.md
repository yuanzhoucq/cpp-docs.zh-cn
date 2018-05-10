---
title: 'Criticalsectiontraits:: Getinvalidvalue 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72c9dce0765029ee31e079315baec72afd16a46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue 方法
专用化 CriticalSection 模板，以便始终无效的模板。  
  
## <a name="syntax"></a>语法  
  
```  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>返回值  
 始终返回一个指向无效的关键部分。  
  
## <a name="remarks"></a>备注  
 *类型*修饰符定义为`typedef CRITICAL_SECTION* Type;`。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)