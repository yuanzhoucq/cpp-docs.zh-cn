---
title: SRWLock 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec31b1469f437ff2776ed9da52fbcd7557fca8e2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="srwlock-class"></a>SRWLock 类
表示精简读取器/编写器锁定。  
  
## <a name="syntax"></a>语法  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>备注  
 精简读取器/编写器锁用于跨到的对象或资源的线程同步访问。 有关详细信息，请参阅[同步函数](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b)。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|||  
|-|-|  
|**SyncLockExclusive**|获取以独占模式的 SRWLock 对象的同义词。|  
|**SyncLockShared**|获取在共享模式下的 SRWLock 对象的同义词。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[SRWLock::SRWLock 构造函数](../windows/srwlock-srwlock-constructor.md)|初始化 SRWLock 类的新实例。|  
|[SRWLock::~SRWLock 析构函数](../windows/srwlock-tilde-srwlock-destructor.md)|取消初始化 SRWLock 类的实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|获取以独占模式的 SRWLock 对象。|  
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|获取在共享模式下的 SRWLock 对象。|  
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|尝试获取当前或指定 SRWLock 对象的排他模式的 SRWLock 对象。|  
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|尝试针对当前或指定 SRWLock 对象获取共享模式的 SRWLock 对象。|  
  
### <a name="protected-data-member"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[SRWLock::SRWLock_ 数据成员](../windows/srwlock-srwlock-data-member.md)|包含当前 SRWLock 对象的基础锁定变量。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SRWLock`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)