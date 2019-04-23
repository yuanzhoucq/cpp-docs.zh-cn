---
title: AsyncResultType 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: d3f99fa85a777ae8361ed6f7cb82fe97ddd8d667
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028047"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 枚举

指定返回的结果类型`GetResults()`方法。

## <a name="syntax"></a>语法

```cpp
enum AsyncResultType;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`MultipleResults`|多个结果，以渐进方式之间提供一套`Start`状态之前`Close()`调用。|
|`SingleResult`|显示后的单个结果`Complete`事件发生。|

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)