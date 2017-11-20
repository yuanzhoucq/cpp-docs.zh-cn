---
title: "Irowsetupdateimpl:: Setdata |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
dev_langs: C++
helpviewer_keywords: SetData method
ms.assetid: 7288a8d1-a7cf-4957-b832-0f3b18fd0da4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e098db995bad0d99e47d6108436a5324d2920e9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimplsetdata"></a>IRowsetUpdateImpl::SetData
设置一个或多个列中的数据值。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 此方法将替代[irowsetchangeimpl:: Setdata](../../data/oledb/irowsetchangeimpl-setdata.md)方法但包含原始数据，以允许即时或延迟处理操作的缓存。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)