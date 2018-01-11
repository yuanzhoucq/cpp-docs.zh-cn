---
title: "MakeAllocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAllocator
dev_langs: C++
helpviewer_keywords: MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 523bcdb17fc0a1b74fe615e5ff15a6fcef99cc32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="makeallocator-class"></a>MakeAllocator 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 类型名称。  
  
 `hasWeakReferenceSupport`  
 `true`若要为支持弱引用; 的对象分配内存`false`为不支持弱引用的对象分配内存。  
  
## <a name="remarks"></a>备注  
 可激活的类，在有无弱引用支持，为分配内存。  
  
 重写 MakeAllocator 类来实现用户定义的内存分配模型。  
  
 MakeAllocator 通常用于防止内存泄漏，如果在构造过程中引发的对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator 构造函数](../windows/makeallocator-makeallocator-constructor.md)|初始化 MakeAllocator 类的新实例。|  
|[MakeAllocator::~MakeAllocator 析构函数](../windows/makeallocator-tilde-makeallocator-destructor.md)|取消初始化 MakeAllocator 类的当前实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[MakeAllocator::Allocate 方法](../windows/makeallocator-allocate-method.md)|分配内存并将其与当前的 MakeAllocator 对象关联。|  
|[MakeAllocator::Detach 方法](../windows/makeallocator-detach-method.md)|解除分配的内存之间的关联[分配](../windows/makeallocator-allocate-method.md)从当前 MakeAllocator 对象的方法。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `MakeAllocator`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)