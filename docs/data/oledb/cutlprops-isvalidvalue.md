---
title: CUtlProps::IsValidValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c806b7fdeae18f53d9f8fd5d012bf67ce8b1ef6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
用于设置属性之前验证值。  
  
## <a name="syntax"></a>语法  
  
```cpp
      virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>参数  
 `iCurSet`  
 属性集数组中; 中的索引如果只有一个属性集，则为零。  
  
 `pDBProp`  
 属性 ID 和中的新值[需要的 DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)结构。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。 默认返回值为`S_OK`。  
  
## <a name="remarks"></a>备注  
 如果你有任何你想要运行上一个值，你将用于设置属性的验证例程，应重写此函数。 例如，无法验证**DBPROP_AUTH_PASSWORD**针对密码表来确定有效的值。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)