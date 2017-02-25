---
title: "CUtlProps::OnInterfaceRequested | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "OnInterfaceRequested 方法"
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CUtlProps::OnInterfaceRequested
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用者调用其中的一个方法创建对象时接口，处理请求可选接口。  
  
## 语法  
  
```  
  
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(  
   REFIID riid  
);  
```  
  
#### 参数  
 `riid`  
 \[in\] 所需IID的接口。  有关详细信息，请参见 `ICommand::Execute` `riid` 参数的描述在 *OLE DB Programmer's Reference* \(在 *MDAC SDK*\)。  
  
## 备注  
 **OnInterfaceRequested** 处理使用者请求可选接口，当使用者调用其中的一个方法创建对象时接口 \(如 **IDBCreateSession**、**IDBCreateCommand**、`IOpenRowset`或 `ICommand`\)。  将请求接口对应的 OLE DB 属性。  例如，如果，使用者请求 **IID\_IRowsetLocate**，**OnInterfaceRequested** 将 **DBPROP\_IRowsetLocate** 接口。  执行在行集合之后维护这正确状态。  
  
 当使用者调用 **IOpenRowset::OpenRowset** 或 `ICommand::Execute`时，调用此方法。  
  
 如果使用者打开对象并请求可选接口，提供程序应将属性与该接口为 `VARIANT_TRUE`。  在提供的程序调用 **执行** 方法之前，为了让属性特定处理中，**OnInterfaceRequested** 调用。  默认情况下，**OnInterfaceRequested** 处理以下接口：  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 如果希望处理其他的接口，请重写位于数据源、会话、命令行集合类或的此函数处理函数。  重写常规\/获得应检查以确保集合属性的接口将属性也设置所有已链接的属性 \(请参见\)。[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)