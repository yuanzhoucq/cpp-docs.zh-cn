---
title: CRowsetImpl::NameFromDBID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 451c5d0474cbd5d72e650648ebd99eb9f2277a66
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
从字符串中提取**DBID**和将其复制到`bstr`中传递。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>参数  
 *pDBID*  
 [in]指向的指针**DBID**要从中提取字符串。  
  
 `bstr`  
 [in]A [CComBSTR](../../atl/reference/ccombstr-class.md)参照来放置一份**DBID**字符串。  
  
 `bIndex`  
 [in]**true**如果索引**DBID**;**false**如果表**DBID**。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。 具体取决于是否**DBID**是表或索引 (由表示`bIndex`)，该方法将任一返回**DB_E_NOINDEX**或**DB_E_NOTABLE**。  
  
## <a name="remarks"></a>备注  
 调用此方法`CRowsetImpl`的实现[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)和[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CRowsetImpl 类](../../data/oledb/crowsetimpl-class.md)