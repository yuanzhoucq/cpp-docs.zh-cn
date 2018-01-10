---
title: "Cdynamicaccessor:: Setblobsizelimit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs: C++
helpviewer_keywords: SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5d683c06283c82e6117893e44def41d09300da0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
以字节为单位设置的最大 BLOB 大小。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void SetBlobSizeLimit(  
   DBLENGTH nBlobSize   
);  
```  
  
#### <a name="parameters"></a>参数  
 `nBlobSize`  
 指定的 BLOB 大小限制。  
  
## <a name="remarks"></a>备注  
 以字节为单位; 设置的最大 BLOB 大小大于此值的列数据将被视为 BLOB。 某些提供程序 （例如 2 GB) 的列提供了极大的大小。 而不是尝试此大小为列分配内存，你通常会尝试将这些列作为 Blob 绑定。 这样你无需分配所有内存，但你仍可以阅读而不必担心截断的所有数据。 但是，在某些情况的下，在其中你可能想要强制`CDynamicAccessor`若要将大型列中其本机数据类型的绑定。 若要执行此操作，调用`SetBlobSizeLimit`之前调用**打开**。  
  
 构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)设置为默认值为 8000 个字节的最大 BLOB 大小。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)