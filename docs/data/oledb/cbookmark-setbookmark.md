---
title: "Cbookmark:: Setbookmark |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: SetBookmark method
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d30e21724bb7ee0d9d2bf7a6a5a094390fff645a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cbookmarksetbookmark"></a>CBookmark::SetBookmark
将复制由引用的书签值`pBuffer`到`CBookmark`缓冲并将缓冲区大小设置为`nSize`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
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