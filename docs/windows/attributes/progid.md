---
title: progid (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514247"
---
# <a name="progid"></a>progid

指定 COM 对象的 ProgID。

## <a name="syntax"></a>语法

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>参数

*名称*<br/>
表示对象的 ProgID。

Progid 提供用于标识 COM/ActiveX 对象的类标识符 (CLSID) 的可读版本。

## <a name="remarks"></a>备注

使用**progid** C++特性可以指定 COM 对象的 progid。 ProgID 的格式为*name1*。 如果未指定 ProgID 的*版本*, 则默认版本为1。 如果未指定*name1*, 则默认名称为*classname。* 如果未指定**progid**并且指定`vi_progid`了, 则将从 `vi_progid`获取 name1, 并追加 (下一个序列号) 版本。

如果使用**progid**的特性块不同时使用**uuid**, 则编译器将检查注册表以查看指定的**progid**是否存在**uuid** 。 如果未指定**progid** , 则将使用版本 (如果创建组件类, 则为 coclass 名称) 来生成**progid**。

**progid**隐含`coclass`属性, 也就是说, 如果指定**progid**, 则与指定`coclass`和**progid**属性相同。

**Progid**特性使类在指定的名称下自动注册。 生成的 .idl 文件将不会显示**progid**值。

如果在使用 ATL 的项目中使用此属性, 则该属性的行为将发生更改。 除了上述行为, 使用此属性指定的信息在`GetProgID`函数中使用, 并`coclass`由属性注入。 有关详细信息, 请参阅[coclass](coclass.md)特性。

## <a name="example"></a>示例

有关**progid**的示例用法, 请参阅[coclass](coclass.md)的示例。

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
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID 密钥](/windows/win32/com/-progid--key)
