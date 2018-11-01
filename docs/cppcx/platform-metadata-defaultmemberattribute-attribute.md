---
title: Platform::Metadata::DefaultMemberAttribute 特性
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
ms.openlocfilehash: a4b3d5e8ab5d6ce254560bc84daceac74e2c9ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486653"
---
# <a name="platformmetadatadefaultmemberattribute-attribute"></a>Platform::Metadata::DefaultMemberAttribute 特性

指示首选函数以在几个可能的重载函数中调用。

## <a name="syntax"></a>语法

```cpp
public ref class DefaultMember abstract : Attribute
```

## <a name="inheritance"></a>继承

[Platform::Object](../cppcx/platform-object-class.md)

[Platform::Metadata::Attribute](../cppcx/platform-metadata-attribute-attribute.md)

### <a name="remarks"></a>备注

将 DefaultMember 特性应用于将由 JavaScript 应用程序使用的方法。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform::Metadata

**元数据：** platform.winmd

## <a name="see-also"></a>请参阅

[Platform::Metadata 命名空间](../cppcx/platform-metadata-namespace.md)