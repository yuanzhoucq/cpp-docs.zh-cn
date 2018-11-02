---
title: v1_enum （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 9771181399a1abaef2e273665e8b267a2065efea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632422"
---
# <a name="v1enum"></a>v1_enum

指示指定的枚举的类型作为 32 位实体而不是 16 位默认传输。

## <a name="syntax"></a>语法

```cpp
[v1_enum]
```

## <a name="remarks"></a>备注

**V1_enum** c + + 属性具有相同的功能[v1_enum](/windows/desktop/Midl/v1-enum) MIDL 特性。

## <a name="example"></a>示例

下面的代码演示的一种用法**v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|枚举的类型|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)