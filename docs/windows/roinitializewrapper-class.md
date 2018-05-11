---
title: RoInitializeWrapper 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a4479686d3ca591a9fdd1c0659549a2e0db6e1c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 类
初始化 Windows 运行时。  
  
## <a name="syntax"></a>语法  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>备注  
 RoInitializeWrapper 是初始化 Windows 运行时并返回指示操作是否成功的 HRESULT 的便利。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper 构造函数](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|初始化 RoInitializeWrapper 类的新实例。|  
|[RoInitializeWrapper::~RoInitializeWrapper 析构函数](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|销毁 RoInitializeWrapper 类的当前实例。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() 运算符](../windows/roinitializewrapper-hresult-parens-operator.md)|检索 RoInitializeWrapper 构造函数生成的 HRESULT。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)