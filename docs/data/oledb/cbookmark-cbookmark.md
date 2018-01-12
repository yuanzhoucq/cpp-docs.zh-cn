---
title: "Cbookmark:: Cbookmark |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
dev_langs: C++
helpviewer_keywords: CBookmark class, constructor
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 63d5bef87a50b5027a743e9927f22c84636c1c9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cbookmarkcbookmark"></a>CBookmark::CBookmark
构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      CBookmark( );   
CBookmark(  
   DBLENGTH nSize   
);  
```  
  
#### <a name="parameters"></a>参数  
 `nSize`  
 [in] 书签缓冲区的大小（以字节为单位）。  
  
## <a name="remarks"></a>备注  
 第一个函数将缓冲区设置为**NULL**和缓冲区大小为 0。 第二个函数将缓冲区大小设置为 `nSize` 并将缓冲区设置为 `nSize` 字节的字节数组。  
  
> [!NOTE]
>  此函数选项仅适用于**CBookmark\<0 >**。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CBookmark 类](../../data/oledb/cbookmark-class.md)