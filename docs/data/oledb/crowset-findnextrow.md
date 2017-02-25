---
title: "CRowset::FindNextRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CRowset.FindNextRow"
  - "CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset::FindNextRow"
  - "CRowset::FindNextRow"
  - "CRowset<TAccessor>::FindNextRow"
  - "CRowset.FindNextRow"
  - "ATL.CRowset<TAccessor>.FindNextRow"
  - "ATL::CRowset<TAccessor>::FindNextRow"
  - "FindNextRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FindNextRow 方法"
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::FindNextRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定后的书签，查找下一匹配行。  
  
## 语法  
  
```  
  
      HRESULT FindNextRow(   
   DBCOMPAREOP op,   
   BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL    
) throw( );  
```  
  
#### 参数  
 `op`  
 \[in\] 使用操作在比较行值。  有关值，请参见 [IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx)。  
  
 `pData`  
 \[in\] 将匹配的值的指针。  
  
 `wType`  
 \[in\] 指示缓冲区部分的值的数据类型。  有关类型指示器的信息，请参见在 *OLE DB 程序员参考中的*[数据类型](https://msdn.microsoft.com/en-us/library/ms723969.aspx) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nLength`  
 \[in\] 长度，以字节为数据值分配的，使用者数据结构。  有关详细信息，请参见 **cbMaxLen** 中显示的 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 中 *OLE DB 程序员参考*。  
  
 `bPrecision`  
 \[in\] 使用的最大值精度，则获取数据时。  只有在 `wType` 为 `DBTYPE_NUMERIC`时使用。  有关详细信息，请参阅《*OLE DB 程序员参考》\) 中的*[涉及 DBTYPE\_NUMERIC 或 DBTYPE\_DECIMAL 的转换](https://msdn.microsoft.com/en-us/library/ms719714.aspx)。  
  
 `bScale`  
 \[in\] 使用的缩放，在获取数据时。  只有在 `wType` 为 `DBTYPE_NUMERIC` 或 **DBTYPE\_DECIMAL**使用。  有关详细信息，请参阅《*OLE DB 程序员参考》\) 中的*[涉及 DBTYPE\_NUMERIC 或 DBTYPE\_DECIMAL 的转换](https://msdn.microsoft.com/en-us/library/ms719714.aspx)。  
  
 *bSkipCurrent*  
 \[in\] 行数从开始搜索的书签的。  
  
 `pBookmark`  
 \[in\] 起始位置的书签。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 此方法要求可选接口 **IRowsetFind**，因此所有的提供程序可能不支持；如果是这样，方法返回 **E\_NOINTERFACE**。  还必须设置**DBPROP\_IRowsetFind**为`VARIANT_TRUE` 在对包含行集合中的 **打开** 表或命令。  
  
 有关用法信息的使用者中书签，请参见 [使用书签](../../data/oledb/using-bookmarks.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [DBBINDING Structures](https://msdn.microsoft.com/en-us/library/ms716845.aspx)