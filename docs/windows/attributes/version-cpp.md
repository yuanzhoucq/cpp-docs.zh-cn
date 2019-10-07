---
title: 版本 (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 9a432267632b1f2a716a833a485b182cd93a27e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514872"
---
# <a name="version-c"></a>version (C++)

标识类的多个版本中的特定版本。

## <a name="syntax"></a>语法

```cpp
[ version("version") ]
```

### <a name="parameters"></a>参数

*版本*<br/>
的版本号`coclass`。 如果未指定, 则将1.0 放置在 .idl 文件中。

## <a name="remarks"></a>备注

**Version** C++特性具有与[版本](/windows/win32/Midl/version)MIDL 特性相同的功能, 并被传递到生成的 .idl 文件。

## <a name="example"></a>示例

有关**版本**的示例用法, 请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**class**、 **struct**|
|**可重复**|No|
|**必需的特性**|**coclass**|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[类特性](class-attributes.md)