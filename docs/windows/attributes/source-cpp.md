---
title: 源 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: 59ed66acbbd6ef876e6052767dc5a5243d4b8dd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476516"
---
# <a name="source-c"></a>source (C++)

在类上，指定连接点的 COM 对象的源接口。 在属性或方法，指示该成员返回的对象或为事件源的变体。

## <a name="syntax"></a>语法

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>参数

*interfaces*<br/>
到类属性，指定将应用源时的一个或多个接口。 源应用到属性或方法时，不使用此参数。

## <a name="remarks"></a>备注

**源**c + + 属性具有相同的功能[源](/windows/desktop/Midl/source)MIDL 特性。

可以使用[默认](default-cpp.md)属性来指定默认源接口的对象。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**， **struct**，**接口**|
|**可重复**|否|
|**必需的特性**|`coclass` （当应用于类或结构）|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[coclass](coclass.md)