---
title: "CDBVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDBVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDBVariant 类"
  - "Variant 数据类型, ODBC"
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDBVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示MFC ODBC选件类的一个不同的数据类型。  
  
## 语法  
  
```  
class CDBVariant  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDBVariant::CDBVariant](../Topic/CDBVariant::CDBVariant.md)|构造 `CDBVariant` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDBVariant::Clear](../Topic/CDBVariant::Clear.md)|清除 `CDBVariant` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDBVariant::m\_dwType](../Topic/CDBVariant::m_dwType.md)|包含当前存储值的数据类型。  键入 `DWORD`。|  
  
### 公共联合成员  
  
|名称|说明|  
|--------|--------|  
|[CDBVariant::m\_boolVal](../Topic/CDBVariant::m_boolVal.md)|包含类型 **BOOL**的值。|  
|[CDBVariant::m\_chVal](../Topic/CDBVariant::m_chVal.md)|包含类型 `unsigned char`的值。|  
|[CDBVariant::m\_dblVal](../Topic/CDBVariant::m_dblVal.md)|包含类型 **double**的值。|  
|[CDBVariant::m\_fltVal](../Topic/CDBVariant::m_fltVal.md)|包含类型 **float**的值。|  
|[CDBVariant::m\_iVal](../Topic/CDBVariant::m_iVal.md)|包含类型 **short**的值。|  
|[CDBVariant::m\_lVal](../Topic/CDBVariant::m_lVal.md)|包含类型 **long**的值。|  
|[CDBVariant::m\_pbinary](../Topic/CDBVariant::m_pbinary.md)|包含指向类型 `CLongBinary`对象。|  
|[CDBVariant::m\_pdate](../Topic/CDBVariant::m_pdate.md)|包含指向类型 **TIMESTAMP\_STRUCT**对象。|  
|[CDBVariant::m\_pstring](../Topic/CDBVariant::m_pstring.md)|包含指向类型 `CString`对象。|  
|[CDBVariant::m\_pstringA](../Topic/CDBVariant::m_pstringA.md)|存储指向ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) 对象。|  
|[CDBVariant::m\_pstringW](../Topic/CDBVariant::m_pstringW.md)|存储指向宽 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 对象。|  
  
## 备注  
 `CDBVariant` 没有基类。  
  
 `CDBVariant` 类似于 [COleVariant](../../mfc/reference/colevariant-class.md);但是，`CDBVariant` 不使用OLE。  `CDBVariant` 以便存储值，而不必担心值的数据类型。  `CDBVariant` 跟踪当前值的数据类型，如联合存储。  
  
 选件类 [CRecordset](../../mfc/reference/crecordset-class.md) 使用在三个成员函数的 `CDBVariant` 对象: `GetFieldValue`、 `GetBookmark`和 `SetBookmark`。  例如，`GetFieldValue` 允许您动态获取列中的数据。  由于列的数据类型不能在运行时知道，`GetFieldValue` 使用一 `CDBVariant` 对象存储数据。  
  
## 继承层次结构  
 `CDBVariant`  
  
## 要求  
 **Header:** afxdb.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)   
 [CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)   
 [CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)