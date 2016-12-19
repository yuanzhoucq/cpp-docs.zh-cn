---
title: "CDaoRelationFieldInfo 结构 | Microsoft Docs"
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
  - "CDaoRelationFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationFieldInfo 结构"
  - "DAO（数据访问对象）, 关系集合"
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRelationFieldInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“CDaoRelationFieldInfo”  结构包含数据访问对象\(DAO\)的关系定义的字段的信息。  
  
## 语法  
  
```  
  
      struct CDaoRelationFieldInfo  
{  
   CString m_strName;           // Primary  
   CString m_strForeignName;    // Primary  
};  
```  
  
#### 参数  
 `m_strName`  
 在关系的主表中的字段名称。  
  
 `m_strForeignName`  
 在关系的外键表中的字段名称。  
  
## 备注  
 DAO 关系对象在主键表中指定字段和外键表中的字段定义关系。  在上面结构定义中对主键的引用指示信息如何在通过获取 `CDaoDatabase` 类的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成员函数中调用 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 对象的 `m_pFieldInfos` 成员中返回。  
  
 关系对象和关系字段对象不有 MFC 类表示。  相反，在 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 类的基本的 MFC DAO 对象下的 DAO 对象包含关系对象的集合，称为关系集合。  反过来说，每个关系对象包含关系字段对象的集合。  每个关系字段对象关联主键表中一个一个字段与外键表中一个字段。  一起考虑，关系字段对象在，每个表中定义字段的一组，一起来定义关系。  `CDaoDatabase` 允许您通过调用 `GetRelationInfo` 成员函数访问关系对象与 `CDaoRelationInfo` 对象。  `CDaoRelationInfo` 对象，然后，它具有数据成员，即 `m_pFieldInfos`，指向 `CDaoRelationFieldInfo` 对象的数组。  
  
 调用存储您感兴趣的关系对象关系集合容器 `CDaoDatabase` 对象的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成员函数。  然后访问 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 对象的 `m_pFieldInfos` 成员。  `CDaoRelationFieldInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoRelationFieldInfo`对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoRelationInfo 结构](../../mfc/reference/cdaorelationinfo-structure.md)