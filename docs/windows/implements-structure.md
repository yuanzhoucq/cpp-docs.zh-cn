---
title: 实现结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31b95901f2c0b7ff210cc8542dce49991a9eef87
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014813"
---
# <a name="implements-structure"></a>Implements 结构
实现`QueryInterface`和`GetIid`指定接口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
### <a name="parameters"></a>参数  
 *I0*  
 第零个接口 id。 （必需）  
  
 *I1*  
 第一个接口 id。 （可选）  
  
 *I2*  
 第二个接口 id。 （可选）  
  
 *I3*  
 第三个接口 id。 （可选）  
  
 *I4*  
 第四个接口 id。 （可选）  
  
 *I5*  
 第五个接口 id。 （可选）  
  
 *I6*  
 第六个接口 id。 （可选）  
  
 *I7*  
 第七个接口 id。 （可选）  
  
 *I8*  
 第八个接口 id。 （可选）  
  
 *I9*  
 第九个接口 id。 （可选）  
  
 *flags*  
 配置标志的类。 一个或多个[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)中指定的枚举[RuntimeClassFlags](../windows/runtimeclassflags-structure.md)结构。  
  
## <a name="remarks"></a>备注  
 派生的指定接口的列表，它实现的帮助程序模板用于`QueryInterface`和`GetIid`。  
  
 每个*I0*通过*I9*接口参数必须或者派生`IUnknown`， `IInspectable`，或者[ChainInterfaces](../windows/chaininterfaces-structure.md)模板。 *标志*参数确定是否为生成支持`IUnknown`或`IInspectable`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`ClassFlags`|`RuntimeClassFlags<WinRt>` 的同义词。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[Implements::CanCastTo 方法](../windows/implements-cancastto-method.md)|获取一个指向指定接口。|  
|[Implements::CastToUnknown 方法](../windows/implements-casttounknown-method.md)|获取一个指针指向基础`IUnknown`接口。|  
|[Implements::FillArrayWithIid 方法](../windows/implements-fillarraywithiid-method.md)|将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。|  
  
### <a name="protected-constants"></a>受保护的常量  
  
|name|描述|  
|----------|-----------------|  
|[Implements::IidCount 常量](../windows/implements-iidcount-constant.md)|存储实现的接口 Id 的数目。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)