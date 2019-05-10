---
title: Platform::IDisposable 接口
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257824"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable 接口

用于释放非托管资源。

## <a name="syntax"></a>语法

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>特性

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>成员

IDisposable 接口从 IUnknown 接口继承。 IDisposable 还具有下列类型的成员：

**方法**

IDisposable 接口具有以下方法。

|方法|描述|
|------------|-----------------|
|释放|用于释放非托管资源。|

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform