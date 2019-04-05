---
title: call_as （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: a0051cdca6673800b37d5733c0b849da24010fcb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023914"
---
# <a name="callas"></a>call_as

使[本地](local-cpp.md)函数以便远程函数调用时，调用本地函数要映射到远程函数。

## <a name="syntax"></a>语法

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>参数

*函数*<br/>
你想要远程函数调用时调用本地函数。

## <a name="remarks"></a>备注

**Call_as** c + + 属性具有相同的功能[call_as](/windows/desktop/Midl/call-as) MIDL 特性。

## <a name="example"></a>示例

下面的代码演示如何使用**call_as**映射不可远程处理函数 (`f1`) 到可远程处理函数 (`Remf1`):

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[本地](local-cpp.md)