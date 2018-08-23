---
title: async_uuid |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.async_uuid
dev_langs:
- C++
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7619868e131476143c144e695e842708d1b54a6b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606440"
---
# <a name="asyncuuid"></a>async_uuid

指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。

## <a name="syntax"></a>语法

```cpp
[async_uuid (
   uuid
)]
```

### <a name="parameters"></a>参数

*uuid*  
一个标识接口的版本的 UUID。

## <a name="remarks"></a>备注

**Async_uuid** c + + 属性具有相同的功能[async_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL 特性。

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

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[接口特性](../windows/interface-attributes.md)  