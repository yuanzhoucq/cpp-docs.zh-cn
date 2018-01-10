---
title: "Irowsetlocateimpl:: Compare |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs: C++
helpviewer_keywords: Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9eaa0aaecd1ff30e51416aaaccebcc8fe6746222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
比较两个的书签。  
  
## <a name="syntax"></a>语法  
  
```  
  
      STDMETHOD ( Compare )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison   
);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)中*OLE DB 程序员参考*。  
  
## <a name="remarks"></a>备注  
 任一书签可以是一种标准 OLE DB 定义[标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx)(**DBBMK_FIRST**， **DBBMK_LAST**，或**DBBMK_INVALID**)。 返回的值`pComparison`指示两个的书签之间的关系：  
  
-   **DBCOMPARE_LT** (`cbBookmark1`早`cbBookmark2`。)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1`等同于`cbBookmark2`。)  
  
-   **DBCOMPARE_GT** (`cbBookmark1`后，将`cbBookmark2`。)  
  
-   **DBCOMPARE_NE** （书签是相同或者未排序）。  
  
-   **DBCOMPARE_NOTCOMPARABLE** （无法相比书签）。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)