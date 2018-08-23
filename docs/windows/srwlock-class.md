---
title: SRWLock 类 |Microsoft Docs
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
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604231"
---
# <a name="srwlock-class"></a>SRWLock 类

表示精简读取器/编写器锁定。

## <a name="syntax"></a>语法

```cpp
class SRWLock;
```

## <a name="remarks"></a>备注

Slim 读取器/编写器锁用于同步跨线程对象或资源的访问。 有关详细信息，请参阅[同步函数](/windows/desktop/Sync/synchronization-functions)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|||
|-|-|
|`SyncLockExclusive`|同义词**SRWLock**获取独占模式下的对象。|
|`SyncLockShared`|同义词**SRWLock**在共享模式下获取的对象。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[SRWLock::SRWLock 构造函数](../windows/srwlock-srwlock-constructor.md)|初始化的新实例**SRWLock**类。|
|[SRWLock::~SRWLock 析构函数](../windows/srwlock-tilde-srwlock-destructor.md)|取消初始化的实例**SRWLock**类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|获取**SRWLock**独占模式下的对象。|
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|获取**SRWLock**在共享模式下的对象。|
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|尝试获取**SRWLock**对象中的当前或指定的排他模式**SRWLock**对象。|
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|尝试获取**SRWLock**对象中的当前或指定的共享模式**SRWLock**对象。|

### <a name="protected-data-member"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[SRWLock::SRWLock_ 数据成员](../windows/srwlock-srwlock-data-member.md)|包含当前的基础锁定变量**SRWLock**对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLock`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)