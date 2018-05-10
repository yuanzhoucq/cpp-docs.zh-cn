---
title: CriticalSection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b5eda8fb22f72bd1f50801f9993b9bd7a864d35
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="criticalsection-class"></a>CriticalSection 类
表示关键部分对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CriticalSection;  
```  
  
## <a name="members"></a>成员  
  
### <a name="constructor"></a>构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSection::CriticalSection 构造函数](../windows/criticalsection-criticalsection-constructor.md)|初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。|  
|[CriticalSection::~CriticalSection 析构函数](../windows/criticalsection-tilde-criticalsection-destructor.md)|取消初始化和销毁当前 CriticalSection 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSection::TryLock 方法](../windows/criticalsection-trylock-method.md)|尝试进入临界区而不阻止。 如果调用成功，则调用线程将获得的关键部分所有权。|  
|[CriticalSection::Lock 方法](../windows/criticalsection-lock-method.md)|等待指定关键部分对象的所有权。 此函数将在授予调用线程所有权时返回。|  
|[CriticalSection::IsValid 方法](../windows/criticalsection-isvalid-method.md)|指示当前的临界部分是否有效。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CriticalSection::cs_ 数据成员](../windows/criticalsection-cs-data-member.md)|声明关键部分数据成员。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)