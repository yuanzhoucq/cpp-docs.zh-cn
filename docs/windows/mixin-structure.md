---
title: "MixIn 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::MixIn
dev_langs: C++
helpviewer_keywords: MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 883e952dde579cce3f5a65ba4a453f98ddbb4740
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mixin-structure"></a>MixIn 结构
确保运行时类先后派生自 Windows 运行时接口（如果有）和经典 COM 接口。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>参数  
 `Derived`  
 从派生的类型[实现](../windows/implements-structure.md)结构。  
  
 `MixInType`  
 基类型。  
  
 `hasImplements`  
 如果 `true` 派生自当前实现基类型，则为 `MixInType`；否则为 `false`。  
  
## <a name="remarks"></a>备注  
 如果从 Windows 运行时和经典 COM 接口派生的类，类声明列表必须先列出任何 Windows 运行时接口，以及然后任何经典 COM 接口。 MixIn 确保以正确顺序指定接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `MixIn`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)