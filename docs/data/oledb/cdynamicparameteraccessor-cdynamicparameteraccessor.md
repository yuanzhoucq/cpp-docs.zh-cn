---
title: "Cdynamicparameteraccessor:: Cdynamicparameteraccessor |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
dev_langs: C++
helpviewer_keywords:
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
ms.assetid: a1cce5e4-dfb9-43a2-bfb8-0435c653674a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e08c26c7ba9d07c5e845aea3443c824498354b74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a>CDynamicParameterAccessor::CDynamicParameterAccessor
构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor( eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>参数  
 `eBlobHandling`  
 指定处理 BLOB 数据的方式。 默认值是**DBBLOBHANDLING_DEFAULT**。 请参阅[cdynamicaccessor:: Setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)有关的说明**DBBLOBHANDLINGENUM**值。  
  
 `nBlobSize`  
 最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为 8000。 请参阅[cdynamicaccessor:: Setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)有关详细信息。  
  
## <a name="remarks"></a>备注  
 请参阅[cdynamicaccessor:: Cdynamicaccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) BLOB 处理的详细信息的构造函数。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)