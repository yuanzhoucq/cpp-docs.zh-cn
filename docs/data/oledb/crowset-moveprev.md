---
title: 'Crowset:: Moveprev |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>.MovePrev
- CRowset.MovePrev
- MovePrev
- CRowset::MovePrev
- ATL.CRowset.MovePrev
- ATL::CRowset<TAccessor>::MovePrev
- ATL::CRowset::MovePrev
- ATL.CRowset<TAccessor>.MovePrev
- CRowset<TAccessor>::MovePrev
dev_langs:
- C++
helpviewer_keywords:
- MovePrev method
ms.assetid: 7ced2bfb-f556-40fc-97ea-0d4e7213e114
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b86a5266faefaacb0df940f51985f1d31dd006b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097141"
---
# <a name="crowsetmoveprev"></a>CRowset::MovePrev
将光标移动到上一记录。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT MovePrev() throw();  
  
```  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求你设置或者**DBPROP_CANFETCHBACKWARDS**或**DBPROP_CANSCROLLBACKWARDS**到`VARIANT_TRUE`之前调用**打开**对表或包含行集的命令。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)