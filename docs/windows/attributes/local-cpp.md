---
title: 本地 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e510e4faa707c954c52ae9daae4c4dc0d4c800dd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057148"
---
# <a name="local-c"></a>local (C++)

接口标头中使用时，可以使用 MIDL 编译器作为标头生成器。 单个函数中使用时，将指定为其生成无存根 （stub） 的本地过程。

## <a name="syntax"></a>语法

```cpp
[local]
```

## <a name="remarks"></a>备注

**本地**c + + 属性具有相同的功能[本地](/windows/desktop/Midl/local)MIDL 特性。

## <a name="example"></a>示例

请参阅[call_as](call-as.md)有关如何使用的示例**本地**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`dispinterface`|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[call_as](call-as.md)