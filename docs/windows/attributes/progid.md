---
title: progid （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 239f50011c91320c2b5e0a96449139e8eeab10ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072858"
---
# <a name="progid"></a>progid

指定 COM 对象的 ProgID。

## <a name="syntax"></a>语法

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>参数

*name*<br/>
表示的对象的 ProgID。

Progid 提供用来标识 COM/ActiveX 对象的类标识符 (CLSID) 的用户可读版本。

## <a name="remarks"></a>备注

**Progid** c + + 属性允许您指定 COM 对象的 ProgID。 ProgID 具有窗体*name1.name2.version*。 如果未指定*版本*ProgID 的默认版本为 1。 如果未指定*name1.name2*，默认名称是*classname.classname*。 如果未指定**progid**并且你指定`vi_progid`， *name1.name2*取自`vi_progid`和 （下一个序列号） 追加版本。

如果使用的特性块**progid**还使用**uuid**，编译器将检查注册表以查看是否**uuid**存在指定**progid**. 如果**progid**未指定，则将使用的版本 （和组件类名称，如果创建组件类） 来生成**progid**。

**progid**意味着`coclass`属性，也就是说，如果您指定**progid**，它是与指定相同的功能`coclass`并**progid**属性。

**Progid**属性会导致自动注册的指定名称的类。 生成的.idl 文件将不会显示**progid**值。

当使用 ATL 的项目中使用此属性时，该属性的行为更改。 除了上述行为，在使用用此特性指定的信息`GetProgID`函数，由注入`coclass`属性。 有关详细信息，请参阅[组件类](coclass.md)属性。

## <a name="example"></a>示例

有关示例，请参阅[组件类](coclass.md)的示例使用**progid**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID 密钥](/windows/desktop/com/-progid--key)
