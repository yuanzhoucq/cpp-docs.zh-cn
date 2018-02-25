---
title: CRowset::FindNextRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs:
- C++
helpviewer_keywords:
- FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3808666693d9a134d6ebcf12333c090cb2ff8ba3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
查找指定的书签之后的下一步的匹配行。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT FindNextRow(DBCOMPAREOP op,   
  BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `op`  
 [in]要在比较行值中使用的操作。 值，请参阅[IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx)。  
  
 `pData`  
 [in]指向要匹配的值的指针。  
  
 `wType`  
 [in]指示缓冲区的值部分的数据类型。 有关类型指示器的信息，请参阅[数据类型](https://msdn.microsoft.com/en-us/library/ms723969.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
 `nLength`  
 [in]使用者数据结构分配数据值的长度，以字节为单位。 有关详细信息，请参阅说明**cbMaxLen**中[DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程序员参考。*  
  
 `bPrecision`  
 [in]在获取数据使用最大精度。 使用仅当`wType`是`DBTYPE_NUMERIC`。 有关详细信息，请参阅[转换涉及 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx)中*OLE DB 程序员参考*。  
  
 `bScale`  
 [in]获取数据时使用的小数位数。 使用仅当`wType`是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 有关详细信息，请参阅[转换涉及 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx)中*OLE DB 程序员参考*。  
  
 *bSkipCurrent*  
 [in]从该处开始搜索书签的行数。  
  
 `pBookmark`  
 [in]要开始搜索位置的书签。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口**IRowsetFind**，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetFind**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
 在使用者中使用书签的信息，请参阅[使用书签](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)