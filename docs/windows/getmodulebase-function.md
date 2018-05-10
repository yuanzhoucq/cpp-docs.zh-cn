---
title: GetModuleBase 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25e4bb6db6114f7d64522dfe145d51ffaabd476a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="getmodulebase-function"></a>GetModuleBase 函数
检索[ModuleBase](../windows/modulebase-class.md)允许递增和递减的引用计数的指针[RuntimeClass](../windows/runtimeclass-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>返回值  
 指向的指针`ModuleBase`对象。  
  
## <a name="remarks"></a>备注  
 此函数在内部用于递增和递减对象引用计数。  
  
 你可以使用此函数通过调用控制引用计数[modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md)和[modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)