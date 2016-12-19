---
title: "IDBInitializeImpl 类 | Microsoft Docs"
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
  - "ATL.IDBInitializeImpl<T>"
  - "ATL::IDBInitializeImpl<T>"
  - "IDBInitializeImpl"
  - "ATL::IDBInitializeImpl"
  - "ATL.IDBInitializeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBInitializeImpl 类"
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBInitializeImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

针对 [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) 接口提供的实现。  
  
## 语法  
  
```  
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### 参数  
 `T`  
 类，从 `IDBInitializeImpl`中派生。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|构造函数。|  
  
### 接口方法  
  
|||  
|-|-|  
|[初始化](../../data/oledb/idbinitializeimpl-initialize.md)|启动提供程序。|  
|[未初始化](../../data/oledb/idbinitializeimpl-uninitialize.md)|停止提供程序。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|数据源标记。|  
|[m\_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|到 DB 属性的实现信息的指针。|  
  
## 备注  
 对数据源对象中强制接口和由枚举数的可选接口。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)