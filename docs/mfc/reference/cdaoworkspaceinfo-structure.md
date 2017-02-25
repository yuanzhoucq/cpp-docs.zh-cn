---
title: "CDaoWorkspaceInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoWorkspaceInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoWorkspaceInfo 结构"
  - "DAO（数据访问对象）, 工作区集合"
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoWorkspaceInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoWorkspaceInfo` 结构包含有关数据访问对象（DAO）定义的数据库对象的信息 。  
  
## 语法  
  
```  
  
      struct CDaoWorkspaceInfo  
{  
   CString m_strName;           // Primary  
   CString m_strUserName;       // Secondary  
   BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一命名工作区对象。  若要直接检索此属性的值，则调用querydef对象的[GetName](../Topic/CDaoQueryDef::GetName.md)成员函数。  有关更多信息，请参见本主题中 DAO 帮助中的“名称属性”。  
  
 *m\_strUserName*  
 表示工作区对象的所有者的值。  有关相关信息，请参见主题“用户名"属性”DAO 帮助。  
  
 *m\_bIsolateODBCTrans*  
 指示是否的值时涉及同一 ODBC 数据库的多个事务隔离。  有关更多信息，请参见 [CDaoWorkspace::SetIsolateODBCTrans](../Topic/CDaoWorkspace::SetIsolateODBCTrans.md)。  有关相关信息，请参见主题“IsolateODBCTrans属性”DAO 帮助。  
  
## 备注  
 工作区是 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)类对象。  附属的引用和所有的指示信息如何由 [GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) 成员函数，在类 `CDaoWorkspace`中。  
  
 [CDaoWorkspace::GetWorkspaceInfo](../Topic/CDaoWorkspace::GetWorkspaceInfo.md) 成员函数检索的信息在 `CDaoWorkspaceInfo` 结构存储。  `CDaoWorkspaceInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoWorkspaceInfo`对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)