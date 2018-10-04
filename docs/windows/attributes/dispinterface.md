---
title: 调度接口 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b02244e0576f99cc0a6940f2ee4a13511cfbe6f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790322"
---
# <a name="dispinterface"></a>dispinterface

将一个接口作为调度接口置于 .idl 文件中。

## <a name="syntax"></a>语法

```cpp
[dispinterface]
```

## <a name="remarks"></a>备注

当 **dispinterface** C++ 属性优先于接口时，会导致将接口置于生成的 .idl 文件中的 library 块中。

除非指定基类，否则调度接口派生自 `IDispatch`。 必须指定[id](id.md)调度接口的成员。

有关用法示例[dispinterface](/windows/desktop/Midl/dispinterface) MIDL 文档中：

```cpp
dispinterface helloPro
   { interface hello; };
```

对于 **dispinterface** 属性无效。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)有关如何使用的示例**dispinterface**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

有关详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[按用法分的特性](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)  