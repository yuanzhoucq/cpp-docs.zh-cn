---
title: usesgetlasterror （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 44a1a55114bcf2466aa5b084f2b53c5457f1a0aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487017"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

告知调用方，是否调用该函数时出现错误，然后调用方可以然后调用`GetLastError`检索错误代码。

## <a name="syntax"></a>语法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>备注

**Usesgetlasterror** c + + 属性具有相同的功能[usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) MIDL 特性。

## <a name="example"></a>示例

请参阅[idl_module](idl-module.md)示例有关的示例中的用法**usesgetlasterror**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**模块**属性|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)