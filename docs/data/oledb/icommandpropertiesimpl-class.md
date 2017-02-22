---
title: "ICommandPropertiesImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandPropertiesImpl"
  - "ATL.ICommandPropertiesImpl"
  - "ATL::ICommandPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandPropertiesImpl 类"
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandPropertiesImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供接口的实现。[ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx)  
  
## 语法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### 参数  
 `T`  
 类，从派生  
  
 `PropClass`  
 属性和类。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|在行集合属性组中返回当前请求行集合属性的列表。|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|在行集合属性组中设置属性。|  
  
## 备注  
 这是强制性上的命令。  [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) 宏定义的静态函数的实现。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)