---
title: "CDaoRelationInfo 结构 | Microsoft Docs"
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
  - "CDaoRelationInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRelationInfo 结构"
  - "DAO（数据访问对象）, 关系集合"
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRelationInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDaoRelationInfo` 结构在 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 对象包含有关信息表之间的关系定义两个字段。  
  
## 语法  
  
```  
  
      struct CDaoRelationInfo  
{  
   CDaoRelationInfo( );                    // Constructor  
   CString m_strName;                      // Primary  
   CString m_strTable;                     // Primary  
   CString m_strForeignTable;              // Primary  
   long m_lAttributes;                     // Secondary  
   CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary  
   short m_nFields;                        // Secondary  
   // Below the // Implementation comment:  
   // Destructor, not otherwise documented  
};  
```  
  
#### 参数  
 `m_strName`  
 唯一命名关系对象。  有关更多信息，请参见本主题中 DAO 帮助中的“名称属性”。  
  
 *m\_strTable*  
 在关系将主表。  
  
 *m\_strForeignTable*  
 在关系将外部资料表。  外表是表中外键。  通常，使用一方面来建立或强制引用完整性。  （外表通常是一对多关系中与许多相对应的表。）  外表包括表的示例包含美国或状态的默认或\/客户订单的代码。  
  
 `m_lAttributes`  
 包含有关项类型的信息。  此值成员可以是以下任何一种操作：  
  
-   **dbRelationUnique** 是一对一的关系。  
  
-   **dbRelationDontEnforce** 关系不会实施 \(并未引用完整性\)。  
  
-   **dbRelationInherited** 关系存在一个附加到的表中使用的数据库。  
  
-   **dbRelationLeft** 关系是左联接。  左外部联接包含任何记录开始 \(左侧\) 两个表，因此，即使没有记录匹配的值。第二个右手表 \(\) 中。  
  
-   **dbRelationRight** 一关系是正确的联接。  右外部联接包含任何记录开始 \(左侧\) 两个表，因此，即使没有记录匹配的值。第一个表 \(左侧\) 中。  
  
-   **dbRelationUpdateCascade** 将级联更新。  
  
-   **dbRelationDeleteCascade** 将级联删除。  
  
 `m_pFieldInfos`  
 指向[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) 结构的数组的指针。  数组位于关系包含每个对象。  `m_nFields` 数据成员为数组元素进行计数。  
  
 `m_nFields`  
 的 `CDaoRelationFieldInfo` 的数字在 `m_pFieldInfos` 数据成员。  
  
## 备注  
 上述主要的和次要的参考指示信息如何由 `CDaoDatabase` 类中的 [GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md) 成员函数返回的。  
  
 关系对象不被 MFC 类表示。  相反，基于 `CDaoDatabase` 类的 MFC 对象的 DAO 对象维护关系对象的集合：`CDaoDatabase` 提供成员函数信息关系访问数组各个项，也可同时访问它们通过调用 `CDaoRelationInfo` 对象所含数据库对象的 `GetRelationInfo` 成员函数。  
  
 [CDaoDatabase::GetRelationInfo](../Topic/CDaoDatabase::GetRelationInfo.md)成员函数检索的信息在`CDaoRelationInfo` 结构存储。  `CDaoRelationInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用`Dump` 显示`CDaoRelationInfo`对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [CDaoRelationFieldInfo 结构](../../mfc/reference/cdaorelationfieldinfo-structure.md)