---
title: "IRowsetIdentityImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetIdentityImpl"
  - "ATL.IRowsetIdentityImpl"
  - "IRowsetIdentityImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetIdentityImpl 类"
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetIdentityImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现 OLE DB 接口，[IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx) 启用行标识的测试。  
  
## 语法  
  
```  
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
#### 参数  
 `T`  
 类从 `IRowsetIdentityImpl` 派生。  
  
 `RowClass`  
 为 **HROW** 的存储单元。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[IsSameRow](../../data/oledb/irowsetidentityimpl-issamerow.md)|比较两个行句柄，以了解它们是否引用了同一个行。|  
  
## 要求  
 **Header:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)