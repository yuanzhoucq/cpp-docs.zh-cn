---
title: com_interface_entry （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 06df146ea47428ee782da7a93c2da7097e110324
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215343"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

将接口条目添加到目标类的 COM 映射。

## <a name="syntax"></a>语法

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>参数

*com_interface_entry*<br/>
一个字符串，其中包含该项的实际文本。 有关可能值的列表，请参阅[COM_INTERFACE_ENTRY 宏](../../atl/reference/com-interface-entry-macros.md)。

## <a name="remarks"></a>备注

**Com_interface_entry** c + + 特性将字符串的 unabridged 内容插入目标对象的 com 接口映射。 如果将特性应用于目标对象一次，则会将该项插入到现有接口映射的开头。 如果该属性重复应用到同一个目标对象，则这些条目将按接收顺序插入到接口映射的开头。

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果 `progid` 应用了，则 `vi_progid` `coclass` 还会应用。

由于**com_interface_entry**的第一次使用导致新接口插入到接口映射的开头，因此它必须是下列 COM_INTERFACE_ENTRY 类型之一：

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

**Com_interface_entry**特性的其他用法可以使用所有支持的 COM_INTERFACE_ENTRY 类型。

此限制是必需的，因为 ATL 在接口映射中使用第一项作为标识 `IUnknown` ; 因此，该项必须是有效接口。 例如，下面的代码示例是无效的，因为接口映射中的第一个条目未指定实际的 COM 接口。

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>示例

下面的代码将两个项添加到的现有 COM 接口映射 `CMyBaseClass` 。 第一个是标准接口，第二个是隐藏 `IDebugTest` 接口。

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

生成的 COM 对象映射如下所示 `CMyBaseClass` ：

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`class`**, **`struct`**|
|**且**|是|
|**必需属性**|以下一项或多项操作： `coclass` 、 `progid` 或 `vi_progid` 。|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)
