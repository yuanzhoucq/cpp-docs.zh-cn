---
title: 'Platform:: recreateexception 方法'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 8173377a3d7a75bc85088037c229bac19f341649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568865"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException 方法

此方法仅供内部使用，不用于用户代码。 请改用 exception:: createexception 方法。

## <a name="syntax"></a>语法

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>参数

*hr*

### <a name="property-valuereturn-value"></a>属性值/返回值

基于指定的 HRESULT 返回新的 Platform::Exception^。
