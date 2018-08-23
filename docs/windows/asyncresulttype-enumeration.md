---
title: AsyncResultType 枚举 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a79ef02302208aa14bc1620e486fcfbc6e12253
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591258"
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

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)