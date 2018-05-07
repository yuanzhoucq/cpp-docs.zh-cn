---
title: 'Crowset:: Movenext |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs:
- C++
helpviewer_keywords:
- MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6c56e3dc53699f47c9dc1061120a201ef5698c04
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
将光标移动到下一条记录。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT MoveNext() throw();HRESULT MoveNext(LONG lSkip,   
   bool bForward= true) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `lSkip`  
 [in]提取前要跳过的行数。  
  
 `bForward`  
 [in]传递**true**向前移动到下一条记录， **false**后移。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。 当已达到行集结尾时，返回**DB_S_ENDOFROWSET**。  
  
## <a name="remarks"></a>备注  
 提取中的下一步顺序行`CRowset`对象，记住以前的位置。 （可选） 你可以选择跳过这些`lSkip`行或向后移动。  
  
 此方法要求你设置以下属性之前调用**打开**对表或命令，其中包含行集：  
  
-   **DBPROP_CANSCROLLBACKWARDS**必须`VARIANT_TRUE`如果`lSkip`< 0  
  
-   **DBPROP_CANFETCHBACKWARDS**必须`VARIANT_TRUE`如果`bForward`= false  
  
 否则为 (如果`lSkip`> = 0 和`bForward`= true)，不需要设置任何其他属性。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)