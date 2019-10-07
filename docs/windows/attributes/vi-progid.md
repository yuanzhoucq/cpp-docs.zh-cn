---
title: vi_progid (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514868"
---
# <a name="vi_progid"></a>vi_progid

指定 ProgID 的与版本无关的形式。

## <a name="syntax"></a>语法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>参数

*名称*<br/>
表示对象的独立于版本的 ProgID。

Progid 提供用于标识 COM/ActiveX 对象的类标识符 (CLSID) 的可读版本。

## <a name="remarks"></a>备注

**Vi_progid** C++特性使你可以为 COM 对象指定独立于版本的 progid。 ProgID 的格式为*name1*。 独立于版本的 ProgID 没有*版本*。 可以同时`progid`在上`coclass`指定和**vi_progid**属性。 如果未指定**vi_progid**, 则与版本无关的 progid 是[progid](progid.md)特性指定的值。

**vi_progid**表示`coclass`属性, 即, 如果指定**vi_progid**, 则与指定`coclass`和**vi_progid**属性相同。

**Vi_progid**特性会使类在指定的名称下自动注册。 生成的 .idl 文件将不会显示 ProgID 值。

在 ATL 项目中, 如果也存在[coclass](coclass.md)特性, 则`GetVersionIndependentProgID`函数将使用指定的 ProgID `coclass` (由特性插入)。

## <a name="example"></a>示例

请参阅[coclass](coclass.md)示例, 了解如何使用**vi_progid**的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**class**、 **struct**|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[ProgID 密钥](/windows/win32/com/-progid--key)
