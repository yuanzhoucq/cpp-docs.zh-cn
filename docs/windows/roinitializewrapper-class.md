---
title: RoInitializeWrapper 类 |Microsoft 文档
ms.custom: ''
ms.date: 05/20/2018
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
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705587"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 类
初始化 Windows 运行时。  
  
## <a name="syntax"></a>语法  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>备注  
 RoInitializeWrapper 是初始化 Windows 运行时并返回指示操作是否成功的 HRESULT 的便利。 由于类析构函数调用`::Windows::Foundation::Uninitialize`的实例`RoInitializeWrapper`必须在全局或顶级范围内声明。  
  
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