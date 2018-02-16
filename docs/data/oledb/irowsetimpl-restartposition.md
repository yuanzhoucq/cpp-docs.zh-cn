---
title: "Irowsetimpl:: Restartposition |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs:
- C++
helpviewer_keywords:
- RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cfdf198b68b3587146ebc4a666ac2e596d05aba
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
将下次提取位置重新定位到其初始位置;即，创建第一个行集时其位置。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[irowset:: Restartposition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 行集位置是不确定直到**getnextrow 时**调用。 你可以向后移动 rowet 中通过调用`RestartPosition`然后提取或向后滚动。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)