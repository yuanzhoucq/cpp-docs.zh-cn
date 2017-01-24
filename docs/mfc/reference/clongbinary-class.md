---
title: "CLongBinary Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "BLOB"
  - "CLongBinary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB（二进制大对象）"
  - "BLOB（二进制大对象）, CLongBinary 类"
  - "CLongBinary 类"
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLongBinary Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

simplifies使用非常大二进制数据对象一起使用\(通常称为BLOBs或“二进制大对象”\)在数据库中。  
  
## 语法  
  
```  
class CLongBinary : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CLongBinary::CLongBinary](../Topic/CLongBinary::CLongBinary.md)|构造 `CLongBinary` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CLongBinary::m\_dwDataLength](../Topic/CLongBinary::m_dwDataLength.md)|在处理在 `m_hData`存储数据对象的字节包含实际大小。|  
|[CLongBinary::m\_hData](../Topic/CLongBinary::m_hData.md)|包含一个Windows `HGLOBAL` 句柄实际图像对象。|  
  
## 备注  
 例如，记录字段在SQL表中可能包含表示图片的位图。  `CLongBinary` 对象存储此类对象并记录其大小。  
  
> [!NOTE]
>  通常，是更好的做法与 [DFX\_Binary](../Topic/DFX_Binary.md) 功能结合现在使用 [CByteArray](../../mfc/reference/cbytearray-class.md)。  您仍可以使用 `CLongBinary`，但是，通常 `CByteArray` 提供更多功能在Win32下，因为不再有大小限制遇到与16位 `CByteArray`。  此建议适用于编程时数据访问对象\(DAO\)以及开放式数据库连接\(odbc）。  
  
 若要使用 `CLongBinary` 对象，声明类型 `CLongBinary` 的字段数据成员在您的记录集选件类的。  当记录集构造，该成员将为记录集选件类的一个嵌入成员，然后构造。  在 `CLongBinary` 构造对象之后，记录字段交换\(rfx\)机制从域加载数据对象位于当前记录在数据源并存储回该录制，则该更新记录时。  RFX查询二进制大对象的大小的数据源，并为它的存储区\(通过 `CLongBinary` 对象的 `m_hData` 数据成员\)和存储 `HGLOBAL` 处理到 `m_hData`的数据。  RFX在 `m_dwDataLength` 数据成员还存储数据对象的实际大小。  与对象中的数据一起使用 `m_hData`，使用通常会使用操作在Windows `HGLOBAL` 处理存储的数据的相同技术。  
  
 在销毁记录集时，还会嵌入 `CLongBinary` 对象，并且，其析构函数释放 `HGLOBAL` 数据处理。  
  
 有关用对象并使用 `CLongBinary`的更多信息，请参见位于 [记录集\(odbc\)](../../data/odbc/recordset-odbc.md) 和 [记录集:处理大数据项\(odbc\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## 要求  
 **Header:** afxdb\_.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)