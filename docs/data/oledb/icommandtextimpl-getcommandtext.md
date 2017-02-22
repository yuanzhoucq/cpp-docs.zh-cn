---
title: "ICommandTextImpl::GetCommandText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCommandText"
  - "ICommandTextImpl.GetCommandText"
  - "ICommandTextImpl::GetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCommandText 方法"
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ICommandTextImpl::GetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过最后一次调用[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)，返回文本命令设置。  
  
## 语法  
  
```  
  
      STDMETHOD(GetCommandText)(   
   GUID * pguidDialect,   
   LPOLESTR * ppwszCommand    
);  
```  
  
#### 参数  
 有关更多信息，请参见*OLE DB 程序员参考*中的[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)。  参数 *pguidDialect* 忽略默认方式。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [ICommandTextImpl 类](../../data/oledb/icommandtextimpl-class.md)