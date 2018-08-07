---
title: Move 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
dev_langs:
- C++
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d058919d0906b458c6c4e81d65c9438c95a22b85
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607298"
---
# <a name="move-function"></a>Move 函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<class T>  
inline typename RemoveReference<T>::Type&& Move(  
   _Inout_ T&& arg  
);  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 自变量类型。  
  
 *arg*  
 要移动的参数。  
  
## <a name="return-value"></a>返回值  
 参数*arg*后引用或右值引用的特点，如果有，已删除。  
  
## <a name="remarks"></a>备注  
 将指定的参数从一个位置移动到另一个。  
  
 有关详细信息，请参阅**移动语义**一部分[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** internal.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)