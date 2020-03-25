---
title: async_uuid （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 537bd6d645532d9d5d20b740125c66f3953239bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168455"
---
# <a name="async_uuid"></a>async_uuid

指定指示 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。

## <a name="syntax"></a>语法

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>parameters

*uuid*<br/>
标识接口版本的 UUID。

## <a name="remarks"></a>备注

**Async_uuid** C++特性具有与[async_uuid](/windows/win32/Midl/async-uuid) MIDL 特性相同的功能。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|`interface`|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**双** **调度接口**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)
