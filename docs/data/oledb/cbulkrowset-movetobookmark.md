---
title: "Cbulkrowset:: Movetobookmark |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs: C++
helpviewer_keywords: MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 883bea68992d646fd7ee82257f794394a1d2ffc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
提取用书签标记的行或距离书签指定偏移量 (`lSkip`) 的行。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT MoveToBookmark(  
   const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `bookmark`  
 [in] 标记要从其提取数据的位置的书签。  
  
 `lSkip`  
 [in] 从书签到目标行的行数。 如果 `lSkip` 为零，则提取的第一行是添加了书签的行。 如果 `lSkip` 为 1，则提取的第一行是位于添加了书签的行后的行。 如果`lSkip`为-1，提取的第一行是在书签的行前的行。  
  
## <a name="return-value"></a>返回值  
 请参阅[irowset:: Getdata](https://msdn.microsoft.com/en-us/library/ms716988.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)