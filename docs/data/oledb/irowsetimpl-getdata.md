---
title: "Irowsetimpl:: Getdata |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
dev_langs: C++
helpviewer_keywords: GetData method [OLE DB]
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0226a9096a93ae1b0e6cd7705fef773a01eea9f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplgetdata"></a>IRowsetImpl::GetData
从行的行集的副本检索数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD( GetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[irowset:: Getdata](https://msdn.microsoft.com/en-us/library/ms716988.aspx)中*OLE DB 程序员参考*。  
  
 某些参数都对应于*OLE DB 程序员参考*参数不同的名称中, 所述**irowset:: Getdata**:  
  
|OLE DB 模板参数|*OLE DB 程序员参考*参数|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|`pData`|  
  
## <a name="remarks"></a>备注  
 此外可以处理数据转换使用 OLE DB 数据转换 DLL。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)