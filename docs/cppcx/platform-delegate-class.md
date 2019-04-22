---
title: Platform::Delegate 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 4116de3240c3ef334db51095997f946731372708
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769233"
---
# <a name="platformdelegate-class"></a>Platform::Delegate 类

表示函数对象。

## <a name="syntax"></a>语法

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>成员

Delegate 类具有从 [Platform::Object Class](../cppcx/platform-object-class.md)派生的 Equals()、GetHashCode() 和 ToString() 方法。

### <a name="remarks"></a>备注

使用 [delegate](../extensions/delegate-cpp-component-extensions.md) 关键字创建委托；不要显式使用 Platform::Delegate。 有关详细信息，请参阅[委托](../cppcx/delegates-c-cx.md)。 有关如何创建和使用委托的示例，请参见 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
