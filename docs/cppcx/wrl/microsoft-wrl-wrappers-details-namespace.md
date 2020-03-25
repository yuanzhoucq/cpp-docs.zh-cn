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
ms.openlocfilehash: 005fa79d413708f630b0a6aebbc06782086c81b3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213754"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 命名空间

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>成员

### <a name="classes"></a>类

|名称|说明|
|----------|-----------------|
|[SyncLockT 类](synclockt-class.md)|表示一个类型，该类型可以采用资源的独占或共享所有权。|
|[SyncLockWithStatusT 类](synclockwithstatust-class.md)|表示一个类型，该类型可以采用资源的独占或共享所有权。|

### <a name="methods"></a>方法

|名称|说明|
|----------|-----------------|
|[CompareStringOrdinal 方法](comparestringordinal-method.md)|比较两个指定的 `HSTRING` 对象，并返回一个整数，指示二者在排序顺序中的相对位置。|

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Wrappers 命名空间](microsoft-wrl-wrappers-namespace.md)
