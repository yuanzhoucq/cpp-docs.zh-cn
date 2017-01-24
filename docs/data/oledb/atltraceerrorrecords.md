---
title: "AtlTraceErrorRecords | Microsoft Docs"
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
  - "ATL.AtlTraceErrorRecords"
  - "ATL::AtlTraceErrorRecords"
  - "AtlTraceErrorRecords"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlTraceErrorRecords 函数"
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AtlTraceErrorRecords
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

false，则返回，转储 OLE DB 错误记录信息转储到设备。  
  
## 语法  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### 参数  
 `hErr`  
 \[in\] `HRESULT` 由 OLE DB 使用者模板成员函数返回。  
  
## 备注  
 如果 `hErr` 不是 `S_OK`时，转储 `AtlTraceErrorRecords` OLE DB 错误记录信息转储到设备 \(输出窗口或文件的 **调试** 选项卡\)。  错误的记录信息，从提供程序获取，包括源行号、、说明、帮助文件、上下文和 GUID 每个错误项的记录。  `AtlTraceErrorRecords` 此信息转储只在调试版本。  在发布版本，它已经过优化的空存根 \(stub\)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)