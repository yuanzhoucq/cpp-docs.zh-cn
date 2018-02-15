---
title: CBookmark::SetBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
dev_langs:
- C++
helpviewer_keywords:
- SetBookmark method
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b90c99cb1d50c4b5544d47d4a5ea926e53ac2fd5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cbookmarksetbookmark"></a>CBookmark::SetBookmark
将复制由引用的书签值`pBuffer`到`CBookmark`缓冲并将缓冲区大小设置为`nSize`。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT SetBookmark(DBLENGTH nSize,  
  BYTE* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *nSize*  
 [in]书签缓冲区的大小。  
  
 `pBuffer`  
 [in]指向包含书签值的字节数组的指针。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此函数选项仅适用于**CBookmark\<0 >**。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)