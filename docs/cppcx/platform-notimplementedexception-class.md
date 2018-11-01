---
title: Platform::NotImplementedException 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::NotImplementedException
- VCCORLIB/Platform::NotImplementedException::NotImplementedException
helpviewer_keywords:
- Platform::NotImplementedException
ms.assetid: 6da26cc2-dde8-4aea-aa85-67aac55cf97b
ms.openlocfilehash: 26e8900a10b25507f5091d9cc1f724c73ece7dfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467580"
---
# <a name="platformnotimplementedexception-class"></a>Platform::NotImplementedException 类

当接口成员在派生类型中未实现时引发。

## <a name="syntax"></a>语法

```cpp
public ref class NotImplementedException : COMException,    IException,    IPrintable,    IEquatable
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