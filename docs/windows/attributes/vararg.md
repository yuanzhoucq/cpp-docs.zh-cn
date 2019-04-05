---
title: vararg （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vararg
helpviewer_keywords:
- vararg attribute
ms.assetid: 20fc3244-18e9-411c-990e-d5b4fa29a570
ms.openlocfilehash: a433522b78424c48c4afe754f7b8337e3952dc8e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037337"
---
# <a name="vararg"></a>vararg

指定该函数采用数目可变的参数。

## <a name="syntax"></a>语法

```cpp
[vararg]
```

## <a name="remarks"></a>备注

**Vararg** c + + 属性具有相同的功能[vararg](/windows/desktop/Midl/vararg) MIDL 特性。

## <a name="example"></a>示例

下面的代码演示的一种用法**vararg**:

```cpp
// cpp_attr_ref_vararg.cpp
// compile with: /LD
#include "unknwn.h"
#include "oaidl.h"
[module(name="MyLibrary")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X : public IUnknown
{
   [vararg] HRESULT Button([in, satype(VARIANT)]SAFEARRAY *psa);
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
[方法特性](method-attributes.md)