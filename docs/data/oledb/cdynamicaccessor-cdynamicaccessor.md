---
title: 'Cdynamicaccessor:: Cdynamicaccessor |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 80446719ac8e523efc5ef885fe55fb89561509e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
实例化和初始化`CDynamicAccessor`对象。  
  
## <a name="syntax"></a>语法  
  
```cpp
      CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>参数  
 `eBlobHandling`  
 指定如何处理二进制大型对象 (BLOB) 数据。 默认值是**DBBLOBHANDLING_DEFAULT**。 请参阅[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)有关的说明**DBBLOBHANDLINGENUM**值。  
  
 `nBlobSize`  
 最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为 8000。 请参阅[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)有关详细信息。  
  
## <a name="remarks"></a>备注  
 如果你使用此构造函数初始化`CDynamicAccessor`对象，你可以指定如何，它将绑定 Blob。 Blob 可以包含如图形，声音，或已编译代码的二进制数据。 默认行为是视为 Blob 列超过 8000 个字节，并尝试将其绑定到`ISequentialStream`对象。 但是，你可以指定不同的值的 BLOB 大小。  
  
 你还可以指定如何`CDynamicAccessor`处理称为 BLOB 数据的列数据： 它可以处理的默认方式中的 BLOB 数据; 它可以跳过 （不会绑定） BLOB 数据; 也可以将 BLOB 数据绑定中提供程序分配的内存。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)