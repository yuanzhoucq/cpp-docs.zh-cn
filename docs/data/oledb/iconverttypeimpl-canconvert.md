---
title: IConvertTypeImpl::CanConvert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6431878d94c4dde469a23808b01381c88a2b33ec
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="iconverttypeimplcanconvert"></a>IConvertTypeImpl::CanConvert
命令或行集上，为提供的可用性的类型转换的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 使用中的 OLE DB 数据转换`MSADC.DLL`。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IConvertTypeImpl 类](../../data/oledb/iconverttypeimpl-class.md)