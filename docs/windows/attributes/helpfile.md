---
title: 帮助文件 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a498cefce01d5a22df5211d0f7bb2f64e3a7b79
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790568"
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

有关详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)  