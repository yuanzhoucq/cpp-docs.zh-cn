---
title: ChainInterfaces 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18814a4ad87cefa39201d369926c0778931d4d64
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861131"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 结构
指定可应用于一组接口 ID 的验证和初始化函数。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>参数  
 `I0`  
 （必需）接口 ID 0。  
  
 `I1`  
 （必需）接口 ID 为 1。  
  
 `I2`  
 （可选）接口 ID 2。  
  
 `I3`  
 （可选）接口 ID 3。  
  
 `I4`  
 （可选）接口 ID 4。  
  
 `I5`  
 （可选）接口 ID 5。  
  
 `I6`  
 （可选）接口 ID 6。  
  
 `I7`  
 （可选）接口 ID 7。  
  
 `I8`  
 （可选）接口 ID 8。  
  
 `I9`  
 （可选）接口 ID 9。  
  
 `DerivedType`  
 派生的类型。  
  
 `BaseType`  
 派生类型的基类型。  
  
 `hasImplements`  
 一个布尔值，如果`true`，这意味着你无法使用[MixIn](../windows/mixin-structure.md)与不是派生的类结构[实现](../windows/implements-structure.md)结构。  
  
## <a name="members"></a>成员  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指示指定的接口 ID 是否可以强制转换为每个由 ChainInterface 模板参数定义专用化。|  
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|将 `I0` 模板参数定义的类型的接口指针转换为指向 IUnknown 的指针。|  
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|通过定义的接口 ID 的存储`I0`指定数组中的接口 Id 的指定位置的模板参数。|  
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|验证模板参数 `I0` 到 `I9` 定义的每个接口是否继承自 IUnknown 和/或 IInspectable，以及验证 `I0` 是否继承自 `I1` 到 `I9`。|  
  
### <a name="protected-constants"></a>受保护的常量  
  
|名称|描述|  
|----------|-----------------|  
|[ChainInterfaces::IidCount 常量](../windows/chaininterfaces-iidcount-constant.md)|模板参数 `I0` 到 `I9` 指定的接口中包含的接口 ID 总数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)