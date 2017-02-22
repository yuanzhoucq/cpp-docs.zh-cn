---
title: "CODBCFieldInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODBCFieldInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CODBCFieldInfo 结构"
  - "ODBC, 数据源信息"
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# CODBCFieldInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CODBCFieldInfo` 结构在 ODBC 数据源中有关字段的信息。  
  
## 语法  
  
```  
  
      struct CODBCFieldInfo  
{  
   CString m_strName;  
   SWORD m_nSQLType;  
   UDWORD m_nPrecision;  
   SWORD m_nScale;  
   SWORD m_nNullability;  
};  
```  
  
#### 参数  
 `m_strName`  
 字段名。  
  
 *m\_nSQLType*  
 字段的SQL数据类型。  这可以是 ODBC SQL 数据类型或一驱动程序特定 SQL 数据类型。  有关有效的 ODBC SQL 数据类型列表，请参见“SQL”[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]数据类型。  有关驱动程序特定 SQL 数据类型的信息，请参见、驱动程序的文档。  
  
 *m\_nPrecision*  
 最大字段的精度。  有关详细信息，请参见“长度、精度、小数位数和显示大小”。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m\_nScale*  
 字段的规模。  有关详细信息，请参见“长度、精度、小数位数和显示大小”[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 *m\_nNullability*  
 字段是否接受空值。  这可以是两值之一：**SQL\_NULLABLE**，如果字段接受空值或 **SQL\_NO\_NULLS** 字段，则不接受空值。  
  
## 备注  
 检索此信息，调用 [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)。  
  
## 要求  
 **标头：** afxdb.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)