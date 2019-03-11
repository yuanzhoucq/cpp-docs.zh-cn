---
title: Platform::Metadata::DefaultMemberAttribute 特性
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::DefaultMemberAttribute
helpviewer_keywords:
- Platform::Metadata::DefaultMemberAttribute Attribute
ms.assetid: d8abda01-c257-4371-aec4-541d4825e0af
ms.openlocfilehash: 754d41a385e2717989e87c0e06a180f02429d2c2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739102"
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
