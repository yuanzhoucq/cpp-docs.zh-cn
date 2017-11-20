---
title: "Iaccessorimpl:: Createaccessor |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
dev_langs: C++
helpviewer_keywords: CreateAccessor method
ms.assetid: f6b92075-c0b8-46ca-8361-026d562d24f5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8dbeec03a5947299bdc5810f0a90bb0c6c81dc47
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iaccessorimplcreateaccessor"></a>IAccessorImpl::CreateAccessor
从一组绑定创建一个访问器。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD(CreateAccessor)(  
   DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IAccessor::CreateAccessor](https://msdn.microsoft.com/en-us/library/ms720969.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IAccessorImpl 类](../../data/oledb/iaccessorimpl-class.md)   
 [Iaccessorimpl:: Addrefaccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)