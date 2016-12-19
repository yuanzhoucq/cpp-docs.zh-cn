---
title: "ISessionPropertiesImpl 类 | Microsoft Docs"
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
  - "ISessionPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISessionPropertiesImpl 类"
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISessionPropertiesImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供接口的实现。[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)  
  
## 语法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### 参数  
 `T`  
 类，从 `ISessionPropertiesImpl`中派生。  
  
 `PropClass`  
 该用户可定义的属性类默认为 `T`。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|在会话属性组中返回在当前会话设置的属性列表。|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|在会话属性组中设置属性。|  
  
## 备注  
 在会话的必需的接口。  此类通过调用静态函数实现会话属性定义中由 [属性集映射](../../data/oledb/begin-propset-map.md)。  在会话类指定属性集映射。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)