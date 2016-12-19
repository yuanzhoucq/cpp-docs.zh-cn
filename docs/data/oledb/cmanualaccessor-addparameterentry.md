---
title: "CManualAccessor::AddParameterEntry | Microsoft Docs"
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
  - "CManualAccessor::AddParameterEntry"
  - "ATL.CManualAccessor.AddParameterEntry"
  - "CManualAccessor.AddParameterEntry"
  - "AddParameterEntry"
  - "ATL::CManualAccessor::AddParameterEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddParameterEntry 方法"
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor::AddParameterEntry
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将参数输入到参数类型结构。  
  
## 语法  
  
```  
  
      void AddParameterEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT   
) throw ( );  
```  
  
#### 参数  
 请参阅在*OLE DB Programmer's Reference* 中 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)。  
  
 `nOrdinal`  
 \[in\] 参数数目。  
  
 `wType`  
 \[in\] 数据类型  
  
 `nColumnSize`  
 \[in\] 列大小 \(以字节为单位\)。  
  
 `pData`  
 \[in\] 到缓冲区中存储的数据的指针。  
  
 `pLength`  
 如果需要的话 \[in\] 为字段长度的指针。  
  
 `pStatus`  
 \[in\] 绑定到变量的指针到列状态，如果必须。  
  
 *eParamIO*  
 \[in\] 指定绑定关联的参数是输入、性能或输出参数。  
  
## 备注  
 若要使用此功能，必须首先调用 [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [DBViewer 示例](../../top/visual-cpp-samples.md)