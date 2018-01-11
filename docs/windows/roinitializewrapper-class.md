---
title: "RoInitializeWrapper 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs: C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f6330c78a6bbac5f14e94c253f05515e3d29575
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)