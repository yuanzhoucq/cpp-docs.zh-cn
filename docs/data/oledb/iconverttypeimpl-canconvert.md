---
title: 'Iconverttypeimpl:: Canconvert |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2f7e32fd01c932f24b617951d601ddcfe7fb5af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IConvertTypeImpl 类](../../data/oledb/iconverttypeimpl-class.md)