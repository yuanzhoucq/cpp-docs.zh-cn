---
title: 'Cenumerator:: Find |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2466127dab53fa6646a4f149400e4318aed59970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
在可用提供程序之间查找指定名称。  
  
## <a name="syntax"></a>语法  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *szSearchName*  
 [in] 要搜索的名称。  
  
## <a name="return-value"></a>返回值  
 **true**如果找到名称。 否则为**false**。  
  
## <a name="remarks"></a>备注  
 此名称将映射到**SOURCES_NAME**的成员[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx)接口。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)