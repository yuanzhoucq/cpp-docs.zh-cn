---
title: appobject （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: 269c5bd3b51e2cc65fbb9c1c7766613595f8b547
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486406"
---
# <a name="appobject"></a>appobject

标识作为应用程序对象，这是与完整.exe 应用程序相关联，指示在此全局可用的函数和属性的组件类组件类[类型库](../../mfc/automation-clients-using-type-libraries.md)。

## <a name="syntax"></a>语法

```cpp
[appobject]
```

## <a name="remarks"></a>备注

**Appobject** c + + 属性具有相同的功能[appobject](/windows/desktop/Midl/appobject) MIDL 特性。

## <a name="example"></a>示例

下面的代码显示了简单的类定义包括特性块的前面**appobject**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|`coclass`|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)