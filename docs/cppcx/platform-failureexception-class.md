---
title: Platform::FailureException 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: b1890fb0649dee779b3851ed9f1fc46a67b2916d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472613"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException 类

操作失败时引发。 它是 E_FAIL HRESULT 的等效项。

## <a name="syntax"></a>语法

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>备注

有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md) 类。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="see-also"></a>请参阅

[Platform::COMException 类](../cppcx/platform-comexception-class.md)