---
title: CAccessorBase::GetHAccessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
dev_langs:
- C++
helpviewer_keywords:
- GetHAccessor method
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a078ddcbeffc96af35274746de8f052cc6c38810
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="caccessorbasegethaccessor"></a>CAccessorBase::GetHAccessor
检索指定访问器的访问器句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp
      HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>参数  
 `nAccessor`  
 [in] 访问器的零偏移量。  
  
## <a name="return-value"></a>返回值  
 访问器句柄。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CAccessorBase 类](../../data/oledb/caccessorbase-class.md)