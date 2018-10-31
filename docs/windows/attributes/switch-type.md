---
title: switch_type （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7aa11ada46f74c3e2a7293c65151b1f1ede7255e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080086"
---
# <a name="switchtype"></a>switch_type

标识用作联合判别变量的类型。

## <a name="syntax"></a>语法

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>参数

*type*<br/>
开关类型可以是整数、 字符、 布尔值或枚举类型。

## <a name="remarks"></a>备注

**Switch_type** c + + 属性具有相同的功能[switch_type](/windows/desktop/Midl/switch-type) MIDL 特性。

不支持 c + + 特性[封装联合](/windows/desktop/Midl/encapsulated-unions)。 [Nonencapsulated 的联合](/windows/desktop/Midl/nonencapsulated-unions)支持仅按以下格式：

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>示例

请参阅[用例](case-cpp.md)的示例使用的示例**switch_type**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**typedef**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)