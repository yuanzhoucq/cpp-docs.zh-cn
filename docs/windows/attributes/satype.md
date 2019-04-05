---
title: satype （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 7588e8d855d648309c46d981898cfbbf7888f4c9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025719"
---
# <a name="satype"></a>satype

指定的数据类型`SAFEARRAY`结构。

## <a name="syntax"></a>语法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>参数

*data_type*<br/>
数据类型为`SAFEARRAY`数据结构是作为参数传递给接口方法。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

## <a name="remarks"></a>备注

**Satype** c + + 属性指定的数据类型`SAFEARRAY`。

> [!NOTE]
> 从删除一定程度的间接性`SAFEARRAY`从它在.cpp 文件中的声明方式生成的.idl 文件中的指针。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[Parameter 特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[id](id.md)