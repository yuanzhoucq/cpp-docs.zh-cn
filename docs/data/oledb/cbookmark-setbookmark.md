---
title: 'Cbookmark:: Setbookmark |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6d8f4402a6caf01f4d813e6ee8f9fd2d95512394
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093672"
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
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)