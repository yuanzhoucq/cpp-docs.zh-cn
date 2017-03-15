---
title: "IRowsetCreatorImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetCreatorImpl"
  - "ATL.IRowsetCreatorImpl"
  - "ATL::IRowsetCreatorImpl<T>"
  - "ATL.IRowsetCreatorImpl<T>"
  - "IRowsetCreatorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetCreatorImpl 类"
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetCreatorImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`IObjectWithSite` 执行与  **相同，而且支持 OLE DB 属性** DBPROPCANSCROLLBACKWARDS 和 DBPROPCANFETCHBACKWARDS。  
  
## 语法  
  
```  
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### 参数  
 `T`  
 从**IRowsetCreator**派生的设备上下文类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|将包含的行集合对象的站点。|  
  
## 备注  
 此类从 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 继承并重写。[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) 尽管提供程序命令或会话对象创建行集合时，它调用在查找 `IObjectWithSite` 的行集合对象的 `QueryInterface` 并调用传递行集合对象的 **IUnkown** 接口的 `SetSite`，当站点接口。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)