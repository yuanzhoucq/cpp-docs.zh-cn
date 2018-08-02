---
title: ChainInterfaces 结构 |Microsoft Docs
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
ms.openlocfilehash: f16a10ef5119730fb492c4adb890aedcc09d3174
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461528"
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
 *I0*  
 （必需）接口 ID 0。  
  
 *I1*  
 （必需）接口 ID 为 1。  
  
 *I2*  
 （可选）接口 ID 为 2。  
  
 *I3*  
 （可选）ID 为 3 的接口。  
  
 *I4*  
 （可选）接口 ID 4。  
  
 *I5*  
 （可选）接口 ID 5。  
  
 *I6*  
 （可选）接口 ID 6。  
  
 *I7*  
 （可选）接口 ID 7。  
  
 *I8*  
 （可选）接口 ID 8。  
  
 *I9*  
 （可选）接口 ID 9。  
  
 *DerivedType*  
 派生的类型。  
  
 *BaseType*  
 派生类型的基类型。  
  
 *hasImplements*  
 一个布尔值，如果 **，则返回 true**，意味着不能使用[MixIn](../windows/mixin-structure.md)不是派生的类结构[实现](../windows/implements-structure.md)结构。  
  
## <a name="members"></a>成员  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指示指定的接口 ID 是否可以转换为每个由 ChainInterface 模板参数定义的专用化。|  
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|定义的类型的接口指针转换*I0*为指向 IUnknown 的模板参数。|  
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|通过定义的接口 ID 的存储*I0*到指定数组中的接口 Id 的指定位置的模板参数。|  
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|验证每个接口定义的模板参数*I0*通过*I9*继承`IUnknown`和/或`IInspectable`，以及*I0*继承*I1*通过*I9*。|  
  
### <a name="protected-constants"></a>受保护的常量  
  
|name|描述|  
|----------|-----------------|  
|[ChainInterfaces::IidCount 常量](../windows/chaininterfaces-iidcount-constant.md)|模板参数所指定的接口中包含的接口 Id 总数*I0*通过*I9*。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)