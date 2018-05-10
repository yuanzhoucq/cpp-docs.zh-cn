---
title: 'Implements:: casttounknown 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 857d13736a92bbbc2c6f1228b3444081ffc18de5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown 方法
获取一个指向基础的 IUnknown 接口。  
  
## <a name="syntax"></a>语法  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>返回值  
 此操作始终成功并返回的 IUnknown 指针。  
  
## <a name="remarks"></a>备注  
 内部帮助程序函数。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Implements 结构](../windows/implements-structure.md)