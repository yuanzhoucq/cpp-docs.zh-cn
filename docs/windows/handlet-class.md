---
title: HandleT 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99a596bf1e086ac7b1a1a72c3504ce4f41844ba4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="handlet-class"></a>HandleT 类
表示对象的句柄。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### <a name="parameters"></a>参数  
 `HandleTraits`  
 实例[HandleTraits](../windows/handletraits-structure.md)定义的句柄的共同特征的结构。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`Traits`|`HandleTraits` 的同义词。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[HandleT::HandleT 构造函数](../windows/handlet-handlet-constructor.md)|初始化 HandleT 类的新实例。|  
|[HandleT::~HandleT 析构函数](../windows/handlet-tilde-handlet-destructor.md)|取消初始化 HandleT 类的实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[HandleT::Attach 方法](../windows/handlet-attach-method.md)|将指定的句柄与当前的 HandleT 对象相关联。|  
|[HandleT::Close 方法](../windows/handlet-close-method.md)|关闭当前的 HandleT 对象。|  
|[HandleT::Detach 方法](../windows/handlet-detach-method.md)|解除关联从其基础句柄当前的 HandleT 对象。|  
|[HandleT::Get 方法](../windows/handlet-get-method.md)|获取基础句柄的值。|  
|[HandleT::IsValid 方法](../windows/handlet-isvalid-method.md)|指示当前 HandleT 对象是否表示句柄。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[HandleT::InternalClose 方法](../windows/handlet-internalclose-method.md)|关闭当前的 HandleT 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[HandleT::operator= 运算符](../windows/handlet-operator-assign-operator.md)|将指定的 HandleT 对象的值移到当前的 HandleT 对象。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[HandleT::handle_ 数据成员](../windows/handlet-handle-data-member.md)|包含由 HandleT 对象的句柄。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `HandleT`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)