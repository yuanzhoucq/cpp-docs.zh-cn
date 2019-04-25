---
title: com_interface_entry (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 65d174679f851613e064568b071cfcbdad8f0f06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148258"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

接口将项添加到目标类的 COM 映射。

## <a name="syntax"></a>语法

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>参数

*com_interface_entry*<br/>
包含的项的实际文本的字符串。 有关可能的值的列表，请参阅[COM_INTERFACE_ENTRY 宏](../../atl/reference/com-interface-entry-macros.md)。

## <a name="remarks"></a>备注

**Com_interface_entry** C++属性将 unabridged 的字符字符串的内容插入到目标对象的 COM 接口映射。 如果该属性一次应用于目标对象，该条目插入到现有的接口映射的开头。 如果该特性重复应用于相同的目标对象，会将条目插入按接收的顺序中的接口映射的开头。

此属性要求 [coclass](coclass.md)、 [progid](progid.md)或 [vi_progid](vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果`progid`应用时，`vi_progid`和`coclass`也会应用。

因为第一个**com_interface_entry**导致新的接口的接口映射开头插入它必须是以下 COM_INTERFACE_ENTRY 类型之一：

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

其他用法**com_interface_entry**属性可以使用所有受支持的 COM_INTERFACE_ENTRY 类型。

此限制是必要的因为 ATL 作为标识接口映射中使用的第一个条目`IUnknown`; 因此，输入项必须是有效的接口。 例如，下面的代码示例无效，因为接口映射中的第一个条目不指定实际的 COM 接口。

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>示例

下面的代码将两个条目添加到现有的 COM 接口映射的`CMyBaseClass`。 第一个是一个标准接口，并第二个隐藏`IDebugTest`接口。

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

为生成的 COM 对象映射`CMyBaseClass`如下所示：

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
|**适用对象**|**类**，**结构**|
|**可重复**|是|
|**必需的特性**|一个或多个以下： `coclass`， `progid`，或`vi_progid`。|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)