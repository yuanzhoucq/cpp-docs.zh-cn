---
title: "CUtlProps 类 | Microsoft Docs"
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
  - "CUtlProps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUtlProps 类"
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现多种 OLE DB 属性接口的属性 \(例如，`IDBProperties`、`IDBProperties`和 `IRowsetInfo`\)。  
  
## 语法  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### 参数  
 `T`  
 包含 `BEGIN_PROPSET_MAP`的类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|从属性集合获取属性。|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|用于在设置属性前验证值。|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|当使用者调用对象创建接口时，的方法处理对可选接口。|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|调用在设置属性后处理链接的属性。|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|将属性设置的属性。|  
  
## 备注  
 此类大部分是执行详细信息。  
  
 `CUtlProps` 内部包含属性设置两个成员：[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) 和 [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)。  
  
 有关使用属性集映射宏的更多信息，请参见 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) 和 [END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md)。  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)