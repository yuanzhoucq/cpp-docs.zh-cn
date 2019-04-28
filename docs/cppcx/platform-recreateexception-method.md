---
title: 'Platform:: recreateexception 方法'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330318"
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
