---
title: AsyncResultType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214157"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 枚举

指定 `GetResults()` 方法返回的结果的类型。

## <a name="syntax"></a>语法

```cpp
enum AsyncResultType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`MultipleResults`|一组多个结果，这些结果在 `Start` 状态之间和在调用 `Close()` 之前逐渐显示。|
|`SingleResult`|在 `Complete` 事件发生后显示的单个结果。|

## <a name="requirements"></a>要求

**标头：** async。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
