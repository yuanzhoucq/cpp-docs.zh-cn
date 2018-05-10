---
title: AsyncResultType 枚举 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de4a8465dd61e52425a0335e171cf516591ae589
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 枚举
指定 GetResults() 方法返回的结果类型。  
  
## <a name="syntax"></a>语法  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>成员  
  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`MultipleResults`|多个结果，以及调用 close （） 之前起始状态之间渐进式呈现一组。|  
|`SingleResult`|在完成事件发生后提供单个结果。|  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)