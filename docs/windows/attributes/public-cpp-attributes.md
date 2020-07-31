---
title: public （c + + 特性）（c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: d5307b96c58492aa06f115ca7a814aa221062e01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224365"
---
# <a name="public-c-attributes"></a>public（C++ 特性）

确保 typedef 将进入类型库，即使它未从 .idl 文件中引用。

## <a name="syntax"></a>语法

```cpp
[public]
```

## <a name="remarks"></a>备注

**`public`** C + + 特性具有与[公共](/windows/win32/Midl/public)MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何使用 **`public`** 特性：

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`typedef`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)
