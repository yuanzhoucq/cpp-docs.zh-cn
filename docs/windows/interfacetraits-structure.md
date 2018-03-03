---
title: "InterfaceTraits 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c28c7c1eef2fc278a0667ec4b7c635005331467
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<  
   typename CloakedType  
>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### <a name="parameters"></a>参数  
 `I0`  
 接口的名称。  
  
 `CloakedType`  
 对于 RuntimeClass、 Implements 和 ChainInterfaces，接口不会在列表中支持接口 Id。  
  
## <a name="remarks"></a>备注  
 实现的接口的共同特征。  
  
 第二个模板是掩蔽接口的专用化。 第三个模板是 Nil 参数的专用化。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`Base`|模板参数 `I0` 的同义词。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指示是否可以强制的指定的指针转换为指向的指针`Base`。|  
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|指向指针的指定的指针转换`Base`。|  
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|为指向 IUnknown 的指定的指针转换。|  
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|将分配的接口 ID`Base`通过索引参数指定的数组元素。|  
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|验证正确派生基。|  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[InterfaceTraits::IidCount 常量](../windows/interfacetraits-iidcount-constant.md)|保存数量的接口 Id 与当前的 InterfaceTraits 对象相关联。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `InterfaceTraits`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)