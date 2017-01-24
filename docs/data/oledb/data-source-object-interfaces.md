---
title: "数据源对象接口 | Microsoft Docs"
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
  - "数据源对象 [C++]"
  - "数据源对象 [C++], 接口"
  - "接口 [C++], 列表"
  - "接口 [C++], OLE DB"
  - "OLE DB [C++], 接口"
  - "OLE DB 提供程序模板 [C++], 对象接口"
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源对象接口
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表显示 OLE DB 为数据源对象定义的强制和可选接口。  
  
|接口|是否必需？|是否由 OLE DB 模板实现？|  
|--------|-----------|----------------------|  
|`IDBCreateSession`|必需|是|  
|`IDBInitialize`|必需|是|  
|`IDBProperties`|必需|是|  
|[\<caps:sentence id\="tgt14" sentenceid\="731a3344bc1c6b5f8f54d9de3524f18a" class\="tgtSentence"\>IPersist\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms688695)|必需|是|  
|[\<caps:sentence id\="tgt17" sentenceid\="63e99e63156fc90f114fa402662387ef" class\="tgtSentence"\>IConnectionPointContainer\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683857)|可选|否|  
|`IDBDataSourceAdmin`|可选|否|  
|`IDBInfo`|可选|否|  
|[\<caps:sentence id\="tgt26" sentenceid\="7e6a12ecd4cb3b1bd45dccf9421ed567" class\="tgtSentence"\>IPersistFile\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms687223)|可选|否|  
|`ISupportErrorInfo`|可选|否|  
  
 数据源对象通过继承来实现 `IDBProperties`、`IDBInitialize` 和 `IDBCreateSession` 接口。  通过从这些实现类之一继承或不继承，可以选择支持附加功能。  如果要支持 `IDBDataSourceAdmin` 接口，则必须从 `IDBDataSourceAdminImpl` 类继承。  
  
## 请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)