---
title: Microsoft::WRL::Wrappers::Details 命名空间
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
ms.openlocfilehash: 09f3fd1011b05e9aee9816663cb5bd1d9e0081e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431871"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 命名空间

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>成员

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[SyncLockT 类](../windows/synclockt-class.md)|表示可能需要排他的类型或共享资源的所有权。|
|[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)|表示可能需要排他的类型或共享资源的所有权。|

### <a name="methods"></a>方法

|名称|描述|
|----------|-----------------|
|[CompareStringOrdinal 方法](../windows/comparestringordinal-method.md)|比较两个指定`HSTRING`对象，并返回一个整数，指示二者在排序顺序中的相对位置。|

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)