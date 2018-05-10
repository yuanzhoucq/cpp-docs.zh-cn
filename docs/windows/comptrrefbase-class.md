---
title: ComPtrRefBase 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13744a1629ede5575dc992ea15b90e22961a8570
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md)类型派生自它，而不仅仅是 ComPtr 所表示的接口。  
  
## <a name="remarks"></a>备注  
 表示类的基类[ComPtrRef](../windows/comptrref-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`InterfaceType`|模板参数的类型的同义词`T`。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable** 运算符](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|将当前强制转换[ptr_](../windows/comptrrefbase-ptr-data-member.md)对指针到-a-指针-到的数据成员 IInspectable 接口。|  
|[ComPtrRefBase::operator IUnknown** 运算符](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|将当前强制转换[ptr_](../windows/comptrrefbase-ptr-data-member.md)对指针到-a-指针-到的数据成员的 IUnknown 接口。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_ 数据成员](../windows/comptrrefbase-ptr-data-member.md)|指向由当前模板参数指定的类型的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)