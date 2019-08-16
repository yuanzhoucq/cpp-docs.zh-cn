---
title: 调度接口C++ (COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 6360c5e97eae19d7b2d74b3b43d4feae07d4b091
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501614"
---
# <a name="dispinterface"></a>dispinterface

将一个接口作为调度接口置于 .idl 文件中。

## <a name="syntax"></a>语法

```cpp
[dispinterface]
```

## <a name="remarks"></a>备注

当 **dispinterface** C++ 属性优先于接口时，会导致将接口置于生成的 .idl 文件中的 library 块中。

除非指定基类，否则调度接口派生自 `IDispatch`。 必须为调度接口的成员指定 [id](id.md) 。

MIDL 文档中的 [dispinterface](/windows/win32/Midl/dispinterface) 用法示例：

```cpp
dispinterface helloPro
   { interface hello; };
```

对于 **dispinterface** 属性无效。

## <a name="example"></a>示例

有关如何使用 [dispinterface](bindable.md) 的示例，请参阅 **bindable**示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**interface**|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[按用法分的特性](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)