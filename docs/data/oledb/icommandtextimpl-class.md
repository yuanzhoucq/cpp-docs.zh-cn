---
title: "ICommandTextImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandText 类"
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ICommandTextImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供了 [ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx) 接口的实现。  
  
## 语法  
  
```  
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### 参数  
 `T`  
 该命令类从 **ICommandTextImpl**派生。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|通过最后一次调用[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)，返回文本命令设置。|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|设置，文本命令替换现有命令文本。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|存储命令文本。|  
  
## 备注  
 在命令的必需的接口。  
  
## 要求  
 **头文件：**altdb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)