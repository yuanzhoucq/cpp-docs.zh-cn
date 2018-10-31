---
title: emitidl （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 520b9bf8d6a71593acd95ebaac98a72036fcabf2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070018"
---
# <a name="emitidl"></a>emitidl

指定是否处理和生成的.idl 文件中放置所有后续的 IDL 特性。

## <a name="syntax"></a>语法

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>参数

*state*<br/>
这些可能值之一： `true`， `false`， `forced`， `restricted`， `push`，或`pop`。

- 如果`true`，在源代码文件中遇到任何 IDL 类别特性放在生成的.idl 文件。 这是默认设置**emitidl**。

- 如果`false`，生成的.idl 文件中未放置在源代码文件中遇到任何 IDL 类别特性。

- 如果`restricted`，允许在文件中，如果没有为 IDL 特性[模块](module-cpp.md)属性。 编译器不生成的.idl 文件。

- 如果`forced`，重写的后续`restricted`特性，这要求文件具有`module`属性是否存在 IDL 特性在文件中。

- `push` 使您能够保存当前**emitidl**设置应用于内部**emitidl**堆栈，并`pop`允许设置**emitidl**到顶部的内部是任何值**emitidl**堆栈。

`defaultimports=`*布尔*\(可选)

- 如果*布尔*是**true**，docobj.idl 导入到生成的.idl 文件。 此外，如果.idl 文件具有相同名称作为.h 文件`#include`到您的源的代码中找到与.h 文件中，相同的目录，则生成的.idl 文件包含该.idl 文件的导入语句。

- 如果*布尔*是**false**，docobj.idl 不会导入生成的.idl 文件。 必须显式导入具有.idl 文件[导入](import.md)。

## <a name="remarks"></a>备注

之后**emitidl**源代码文件中遇到 c + + 特性、 IDL 类别特性放在生成的.idl 文件。 如果没有任何**emitidl**特性，源代码文件中的 IDL 特性将输出到生成的.idl 文件。

可以有多个**emitidl**源代码文件中的属性。 如果`[emitidl(false)];`在没有后续的文件中遇到`[emitidl(true)];`，则没有属性处理到生成的.idl 文件。

编译器遇到新的文件，每次**emitidl**隐式设置为**true**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)
