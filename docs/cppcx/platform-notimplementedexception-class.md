---
title: 'Platform:: notimplementedexception 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::NotImplementedException
- VCCORLIB/Platform::NotImplementedException::NotImplementedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::NotImplementedException
ms.assetid: 6da26cc2-dde8-4aea-aa85-67aac55cf97b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac52615a9cc00a3fbfdb253e44c7ce5d239009a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103679"
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