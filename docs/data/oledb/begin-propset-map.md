---
title: "BEGIN_PROPSET_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BEGIN_PROPSET_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROPSET_MAP 宏"
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# BEGIN_PROPSET_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记属性集映射项的开始。  
  
## 语法  
  
```  
  
BEGIN_PROPSET_MAP(  
Class   
)  
  
```  
  
#### 参数  
 *类*  
 \[in\] 此设置的属性指定。类。  属性集下 OLE DB 对象可以指定：  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="75bbb794f21139fcd243c18fff6050d2" class\="tgtSentence"\>对象数据源\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="e423b0fba10fc83bd76e01e3eee2fd69" class\="tgtSentence"\>会话对象\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="5f6bc08c46cee6f21bfcdd08aff6e8aa" class\="tgtSentence"\>命令\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## 示例  
 这是该属性集映射：  
  
 [!CODE [NVC_OLEDB_Provider#3](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Provider#3)]  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)