---
title: "Idbcreatesessionimpl:: Createsession |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs: C++
helpviewer_keywords: CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cee8a99e39434ddab7061c2e67adafbeb864717
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
从数据源对象创建新的会话并在新创建的会话上返回所请求的接口。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD(CreateSession)(   
   IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession    
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [IDBCreateSessionImpl 类](../../data/oledb/idbcreatesessionimpl-class.md)