---
title: 'Crowset:: Movetobookmark |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9f638f928c9fee0383e5ed50cd4b3dd547ad4939
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097791"
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
提取用书签标记的行或距离书签指定偏移量 (`lSkip`) 的行。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,   
   LONG lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `bookmark`  
 [in] 标记要从其提取数据的位置的书签。  
  
 `lSkip`  
 [in] 从书签到目标行的行数。 如果 `lSkip` 为零，则提取的第一行是添加了书签的行。 如果 `lSkip` 为 1，则提取的第一行是位于添加了书签的行后的行。 如果`lSkip`为-1，提取的第一行是在书签的行前的行。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetLocate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetLocate**到`VARIANT_TRUE`并设置**DBPROP_CANFETCHBACKWARDS**到`VARIANT_TRUE`之前调用**打开**对表或命令包含行集。  
  
 在使用者中使用书签的信息，请参阅[使用书签](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)