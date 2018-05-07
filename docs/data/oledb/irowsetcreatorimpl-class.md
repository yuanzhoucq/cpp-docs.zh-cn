---
title: IRowsetCreatorImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0492994193130ffa6a547691490b4da1ae557c8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 类
执行与相同的功能`IObjectWithSite`但使 OLE DB 属性还**DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**。  
  
## <a name="syntax"></a>语法

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类**IRowsetCreator**。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|设置包含行集对象的站点。|  
  
## <a name="remarks"></a>备注  
 此类继承自[IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)和替代[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。 当提供程序命令或会话对象创建一个行集合时，它将调用`QueryInterface`寻找行集对象上`IObjectWithSite`和调用`SetSite`将行集对象传递**IUnkown**作为站点接口的接口。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)