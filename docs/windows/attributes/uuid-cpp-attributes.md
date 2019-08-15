---
title: uuid（C++ 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514948"
---
# <a name="uuid-c-attributes"></a>uuid（C++ 特性）

指定类或接口的唯一 ID。

## <a name="syntax"></a>语法

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>参数

*uuid*<br/>
128位的唯一标识符。

## <a name="remarks"></a>备注

如果接口或类的定义未指定**uuid** C++属性, 则 Microsoft C++编译器将提供一个属性。 指定**uuid**时, 必须包含引号。

如果未指定**uuid**, 则编译器将为计算机上不同的属性项目中的相同名称的接口或类生成相同的 GUID。

可以使用 Uuidgen.exe 或 Guidgen.exe 来生成自己的唯一 Id。 (若要运行这两种工具, 请单击 "**开始**", 然后单击菜单上的 "**运行**"。 然后输入所需工具的名称。)

在不使用 ATL 的项目中使用时, 指定**uuid**属性与指定[uuid](../../cpp/uuid-cpp.md) **__declspec**修饰符相同。 若要检索类的**uuid** , 可以使用[__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>示例

有关**uuid**的示例用法, 请参阅可[绑定](bindable.md)示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**类**、**结构**、**接口**、**联合**、**枚举**|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)