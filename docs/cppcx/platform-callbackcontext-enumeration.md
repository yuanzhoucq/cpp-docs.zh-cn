---
title: Platform::CallbackContext 枚举
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 1daa3988fcb985dab9d3083233a3703a20cc2fdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214251"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 枚举

指定在其中执行回调函数（事件处理程序）的线程上下文。

## <a name="syntax"></a>语法

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>成员

|类型代码|说明|
|---------------|-----------------|
|Any|回调函数可以在任何线程上下文上执行。|
|相同|回调函数只能在启动了异步操作的线程上下文上执行。|

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd
