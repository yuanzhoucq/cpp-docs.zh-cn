---
title: local （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: d3710eee748a43a1daa5c07d8b3feb6beb8f64fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214742"
---
# <a name="local-c"></a>local (C++)

在 interface 标头中使用时，允许将 MIDL 编译器用作标头生成器。 在单独的函数中使用时，指定不会为其生成存根的本地过程。

## <a name="syntax"></a>语法

```cpp
[local]
```

## <a name="remarks"></a>备注

**本地** C++特性具有与[本地](/windows/win32/Midl/local)MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**local**的示例，请参阅[call_as](call-as.md) 。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**、interface 方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`dispinterface`|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[call_as](call-as.md)
