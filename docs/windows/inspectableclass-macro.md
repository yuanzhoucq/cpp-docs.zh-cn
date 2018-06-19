---
title: InspectableClass 宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 922f7f74771125aed0122c408ef902da2569e5c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873766"
---
# <a name="inspectableclass-macro"></a>InspectableClass 宏
设置运行时类名称和信任级别。  
  
## <a name="syntax"></a>语法  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>参数  
 `runtimeClassName`  
 运行时类的完整文本名称。  
  
 `trustLevel`  
 之一[TrustLevel](http://msdn.microsoft.com/library/br224625.aspx)枚举值。  
  
## <a name="remarks"></a>备注  
 `InspectableClass`宏可以只能与 Windows 运行时类型一起使用。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)