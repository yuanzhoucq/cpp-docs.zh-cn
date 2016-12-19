---
title: "事务对象接口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "接口, 列表"
  - "接口, OLE DB"
  - "OLE DB 提供程序模板, 对象接口"
  - "OLE DB 提供程序, 事务支持"
  - "OLE DB, 接口"
  - "事务对象接口"
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事务对象接口
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

事务对象定义数据源上的原子工作单元并确定这些工作单元如何相关。  此对象不直接受 OLE DB 提供程序模板的支持（即您必须创建自己的对象）。  
  
 下表显示 OLE DB 为事务对象定义的强制和可选接口。  
  
|接口|是否必需？|是否由 OLE DB 模板实现？|  
|--------|-----------|----------------------|  
|[\<caps:sentence id\="tgt7" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|必需|否|  
|[\<caps:sentence id\="tgt10" sentenceid\="f5097e646bb93cceb560c38e13953a89" class\="tgtSentence"\>ITransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|必需|否|  
|[\<caps:sentence id\="tgt13" sentenceid\="130702210bcc45e1afd88b1f2aae1a0b" class\="tgtSentence"\>ISupportErrorInfo\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|可选|否|  
  
## 请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)