---
title: 'Crowset:: Close |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::Close
- ATL.CRowset.Close
- CRowset<TAccessor>::Close
- CRowset<TAccessor>.Close
- ATL.CRowset<TAccessor>.Close
- ATL::CRowset::Close
- ATL::CRowset<TAccessor>::Close
- CRowset.Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 966d779e-e148-4dc0-bbba-7cfb9fa6a16b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b56cd48a61ceab242081c1323a267b21be661ad4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096725"
---
# <a name="crowsetclose"></a>CRowset::Close
释放行和当前[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)接口。  
  
## <a name="syntax"></a>语法  
  
```cpp
void Close() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 此方法释放行集合中当前包含的所有行。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)