---
title: 'Handletraits:: Getinvalidvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4690daabd84b8127913af0a96d5b929ee986e77
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651228"
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue 方法
表示无效句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline static HANDLE GetInvalidValue();  
```  
  
## <a name="return-value"></a>返回值  
 始终返回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 定义由 Windows 中）。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [HANDLETraits 结构](../windows/handletraits-structure.md)