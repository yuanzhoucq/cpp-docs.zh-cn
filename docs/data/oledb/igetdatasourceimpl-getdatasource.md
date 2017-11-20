---
title: "Igetdatasourceimpl:: Getdatasource |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs: C++
helpviewer_keywords: GetDataSource method
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58dd4fc6e4a7cbe245d8ea1ec5841f5983354f5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="igetdatasourceimplgetdatasource"></a>IGetDataSourceImpl::GetDataSource
返回创建了会话的数据源对象上的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD(GetDataSource)(   
   REFIID riid,   
   IUnknown ** ppDataSource    
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 如果你需要访问数据源对象中的属性很有用。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IGetDataSourceImpl 类](../../data/oledb/igetdatasourceimpl-class.md)