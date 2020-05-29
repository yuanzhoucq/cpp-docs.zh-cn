---
title: satype （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166271"
---
# <a name="satype"></a>satype

指定 `SAFEARRAY` 结构的数据类型。

## <a name="syntax"></a>语法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>parameters

data_type<br/>
作为参数传递给接口方法的 `SAFEARRAY` 数据结构的数据类型。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|Interface 参数，interface 方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

## <a name="remarks"></a>备注

**Satype** C++属性指定 `SAFEARRAY`的数据类型。

> [!NOTE]
> 将从生成的 .idl 文件中的 `SAFEARRAY` 指针中删除间接级别，并从该文件中的声明方式。

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

## <a name="see-also"></a>另请参阅

[编译器特性](compiler-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[id](id.md)
