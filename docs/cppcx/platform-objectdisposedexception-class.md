---
title: Platform::ObjectDisposedException 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ObjectDisposedException
- VCCORLIB/Platform::ObjectDisposedException::ObjectDisposedException
helpviewer_keywords:
- Platform::ObjectDisposedException
ms.assetid: 68506fe4-d09c-4407-999f-1e3edb261d41
ms.openlocfilehash: 41afe11efa23a3418ec9629a3c6f5a45015e2aa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612948"
---
# <a name="platformobjectdisposedexception-class"></a>Platform::ObjectDisposedException 类

对已释放对象执行操作时引发。

## <a name="syntax"></a>语法

```cpp
public ref class ObjectDisposedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>备注

有关更多信息，请参见 [COMException](../cppcx/platform-comexception-class.md)。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="see-also"></a>请参阅

[Platform::COMException 类](../cppcx/platform-comexception-class.md)