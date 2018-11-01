---
title: async_uuid （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 559500a1390e0d1bac8344d0ffcfc1bdd9ad55f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490904"
---
# <a name="asyncuuid"></a>async_uuid

指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。

## <a name="syntax"></a>语法

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>参数

*uuid*<br/>
一个标识接口的版本的 UUID。

## <a name="remarks"></a>备注

**Async_uuid** c + + 属性具有相同的功能[async_uuid](/windows/desktop/Midl/async-uuid) MIDL 特性。

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
|**无效的特性**|**双**，**调度接口**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)