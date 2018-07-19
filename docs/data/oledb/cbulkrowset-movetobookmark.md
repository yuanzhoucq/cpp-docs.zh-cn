---
title: 'Cbulkrowset:: Movetobookmark |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b1911fe170262e65ef06e65649f837a0b723d05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094642"
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
提取用书签标记的行或距离书签指定偏移量 (`lSkip`) 的行。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `bookmark`  
 [in] 标记要从其提取数据的位置的书签。  
  
 `lSkip`  
 [in] 从书签到目标行的行数。 如果 `lSkip` 为零，则提取的第一行是添加了书签的行。 如果 `lSkip` 为 1，则提取的第一行是位于添加了书签的行后的行。 如果`lSkip`为-1，提取的第一行是在书签的行前的行。  
  
## <a name="return-value"></a>返回值  
 请参阅[irowset:: Getdata](https://msdn.microsoft.com/en-us/library/ms716988.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBulkRowset 类](../../data/oledb/cbulkrowset-class.md)