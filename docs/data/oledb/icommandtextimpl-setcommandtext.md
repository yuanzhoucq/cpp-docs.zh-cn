---
title: "ICommandTextImpl::SetCommandText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandTextImpl.SetCommandText"
  - "ICommandTextImpl::SetCommandText"
  - "SetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommandText 方法"
ms.assetid: 7271bfb0-7a8b-4281-b3e8-7c80b9fe79d4
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ICommandTextImpl::SetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置，文本命令替换现有命令文本。  
  
## 语法  
  
```  
  
      STDMETHOD(SetCommandText)(   
   REFGUID rguidDialect,   
   LPCOLESTR pwszCommand    
);  
```  
  
#### 参数  
 有关更多信息，请参见*OLE DB 程序员参考*中的[ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [ICommandTextImpl 类](../../data/oledb/icommandtextimpl-class.md)   
 [ICommandTextImpl::GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)