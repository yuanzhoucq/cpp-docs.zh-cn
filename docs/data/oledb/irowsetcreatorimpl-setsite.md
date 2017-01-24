---
title: "IRowsetCreatorImpl::SetSite | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetCreatorImpl.SetSite"
  - "IRowsetCreatorImpl<T>::SetSite"
  - "IRowsetCreatorImpl::SetSite"
  - "SetSite"
  - "ATL.IRowsetCreatorImpl.SetSite"
  - "ATL::IRowsetCreatorImpl<T>::SetSite"
  - "ATL::IRowsetCreatorImpl::SetSite"
  - "ATL.IRowsetCreatorImpl<T>.SetSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetSite 方法"
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetCreatorImpl::SetSite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将包含的行集合对象的站点。  有关更多信息，请参见 [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  
  
## 语法  
  
```  
  
      STDMETHOD( SetSite )(  
   IUnknown* pCreator   
);  
```  
  
#### 参数  
 `pCreator`  
 \[in\] 用于管理行集合对象的站点的 **IUnknown** 接口指针的指针。  
  
## 返回值  
 标准 `HRESULT`。  
  
## 备注  
 此外，`IRowsetCreatorImpl::SetSite` 以实现 OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS** 属性。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetCreatorImpl 类](../../data/oledb/irowsetcreatorimpl-class.md)