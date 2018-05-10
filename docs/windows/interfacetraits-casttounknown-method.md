---
title: 'Interfacetraits:: Casttounknown 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2fdc46f57f834c3e8217049574ea504aae16f03
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 参数的类型`ptr`。  
  
 `ptr`  
 指针类型`T`。  
  
## <a name="return-value"></a>返回值  
 指向 IUnknown 从中`Base`派生。  
  
## <a name="remarks"></a>备注  
 为指向 IUnknown 的指定的指针转换。  
  
 有关详细信息`Base`，请参阅中的公共 Typedef 部分[InterfaceTraits 结构](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)