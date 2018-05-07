---
title: 'Crowset:: Compare |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>.Compare
- CRowset<TAccessor>::Compare
- ATL.CRowset<TAccessor>.Compare
- ATL::CRowset<TAccessor>::Compare
- CRowset.Compare
- ATL::CRowset::Compare
- ATL.CRowset.Compare
- CRowset::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 56e438e89cc41f124ea8678761d00d647d489466
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetcompare"></a>CRowset::Compare
比较两个书签使用[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Compare(const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 *Bookmark1*  
 [in]要比较的第一个书签。  
  
 *Bookmark2*  
 [in]要比较的第二个书签。  
  
 `pComparison`  
 [out]指向比较的结果的指针。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetLocate`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetLocate**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
 在使用者中使用书签的信息，请参阅[使用书签](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)