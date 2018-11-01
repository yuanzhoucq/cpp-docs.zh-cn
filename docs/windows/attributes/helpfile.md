---
title: 帮助文件 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 594ab4d02065e9b4efe1142c5ced9b76642e5481
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488044"
---
# <a name="helpfile"></a>helpfile

设置类型库的帮助文件的名称。

## <a name="syntax"></a>语法

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>参数

*filename*<br/>
包含的帮助主题文件的名称。

## <a name="remarks"></a>备注

**Helpfile** c + + 属性具有相同的功能[helpfile](/windows/desktop/Midl/helpfile) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[模块](module-cpp.md)有关如何使用的示例**helpfile**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**， **typedef**，**类**，方法中，**属性**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)