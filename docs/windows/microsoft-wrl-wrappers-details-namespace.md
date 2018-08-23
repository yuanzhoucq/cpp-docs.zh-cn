---
title: Microsoft::WRL::Wrappers::Details Namespace |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3af5add0a934b59cf3027b7beb0ea000a7ae1415
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595702"
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