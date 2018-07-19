---
title: 'Caccessorbase:: Isautoaccessor |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs:
- C++
helpviewer_keywords:
- IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabf5d182b6fb0eb993300e241ae76e1b61f5cef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089293"
---
# <a name="caccessorbaseisautoaccessor"></a>CAccessorBase::IsAutoAccessor
如果自动检索数据访问器在移动操作期间，则返回 true。  
  
## <a name="syntax"></a>语法  
  
```cpp
      bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>参数  
 `nAccessor`  
 [in] 访问器的零偏移量。  
  
## <a name="return-value"></a>返回值  
 返回**true**如果访问器为自动访问器。 否则，返回 **false**。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)