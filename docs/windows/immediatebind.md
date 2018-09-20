---
title: immediatebind |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.immediatebind
dev_langs:
- C++
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc4c42132b2b964d0606fc3287e9d9fd98d64370
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400727"
---
# <a name="immediatebind"></a>immediatebind

指示数据库将立即收到通知的所有更改将数据绑定对象的属性。

## <a name="syntax"></a>语法

```cpp
[immediatebind]
```

## <a name="remarks"></a>备注

**Immediatebind** c + + 属性具有相同的功能[immediatebind](/windows/desktop/Midl/immediatebind) MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](../windows/bindable.md)有关如何使用的示例**immediatebind**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[方法特性](../windows/method-attributes.md)<br/>
[defaultbind](../windows/defaultbind.md)<br/>
[displaybind](../windows/displaybind.md)<br/>
[requestedit](../windows/requestedit.md)  