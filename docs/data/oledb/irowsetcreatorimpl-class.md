---
title: "IRowsetCreatorImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs: C++
helpviewer_keywords: IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3a1a1c17ad9469ff31b5520ffadb3349f86827ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl 类
执行与相同的功能`IObjectWithSite`但使 OLE DB 属性还**DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**。  
  
## <a name="syntax"></a>语法  
  
```  
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
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)