---
title: "Cdynamicaccessor:: Setblobhandling |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 21a877cb3aa3d6ff96521348350857c141b8e7b0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
设置处理的当前行值的 BLOB。  
  
## <a name="syntax"></a>语法  
  
```cpp
      bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>参数  
 `eBlobHandling`  
 指定处理 BLOB 数据的方式。 它可以采用以下值：  
  
-   **DBBLOBHANDLING_DEFAULT**： 处理列数据大于`nBlobSize`(通过设置，如同`SetBlobSizeLimit`) 作为 BLOB 数据，然后检索其传递`ISequentialStream`或`IStream`对象。 此选项将尝试将每个列包含大于大小的数据绑定`nBlobSize`或列出为**DBTYPE_IUNKNOWN**作为 BLOB 数据。  
  
-   **DBBLOBHANDLING_NOSTREAMS**： 处理列数据大于`nBlobSize`(通过设置，如同`SetBlobSizeLimit`) 作为 BLOB 数据，然后检索通过提供程序分配，使用者拥有内存中的引用。 此选项可用于具有多个 BLOB 列的表和提供程序仅支持一个`ISequentialStream`每个访问器的对象。  
  
-   **DBBLOBHANDLING_SKIP**： 跳过 （不绑定） 限定为包含 Blob 的列 （访问器将不绑定或检索列的值，但它仍将检索的列状态和长度）。  
  
## <a name="remarks"></a>备注  
 应调用`SetBlobHandling`之前调用**打开**。  
  
 构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)设置处理到值的 BLOB **DBBLOBHANDLING_DEFAULT**。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)