---
title: "Crowset:: Movefirst |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>::MoveFirst
- ATL::CRowset::MoveFirst
- CRowset<TAccessor>.MoveFirst
- CRowset::MoveFirst
- CRowset.MoveFirst
- ATL.CRowset.MoveFirst
- ATL.CRowset<TAccessor>.MoveFirst
- ATL::CRowset<TAccessor>::MoveFirst
dev_langs: C++
helpviewer_keywords: MoveFirst method
ms.assetid: a17c0799-ead9-4d85-9a1d-8b17188d01e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 405549f94e5aad7ea241a5b6ed4687084aa73ff0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovefirst"></a>CRowset::MoveFirst
将光标移到初始位置，并检索初始行。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT MoveFirst( ) throw( );  
  
```  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 调用[irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)来重新定位的下一步提取位置，使其初始位置 （行集创建时的下一步提取位置的位置），并检索初始行。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)   
 [Crowset:: Movenext](../../data/oledb/crowset-movenext.md)   
 [Crowset:: Movetobookmark](../../data/oledb/crowset-movetobookmark.md)   
 [Crowset:: Moveprev](../../data/oledb/crowset-moveprev.md)   
 [Crowset:: Movelast](../../data/oledb/crowset-movelast.md)   
 [Irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)