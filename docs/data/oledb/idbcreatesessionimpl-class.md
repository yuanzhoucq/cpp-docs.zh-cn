---
title: IDBCreateSessionImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 02701b03de074823da3cc7fcd229056195fd9a85
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269454"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl 类
提供一个实现[IDBCreateSession](https://msdn.microsoft.com/library/ms724076.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自  
  
 *SessionClass*  
 会话对象中。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h 
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[CreateSession](#createsession)|从数据源对象创建一个新的会话并返回所请求的接口上新创建的会话。|  
  
## <a name="remarks"></a>备注  
 数据源对象上的必需接口。  

## <a name="createsession"></a> Idbcreatesessionimpl:: Createsession
从数据源对象创建一个新的会话并返回所请求的接口上新创建的会话。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[idbcreatesession:: Createsession](https://msdn.microsoft.com/library/ms714942.aspx)中*OLE DB 程序员参考*。   
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
