---
title: pointer_default （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e8ddf566082bfded1f20a2bfe04e7cef0b5dc14
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790326"
---
# <a name="pointerdefault"></a>pointer_default

指定所有指针，除顶级指针在参数列表中显示的默认指针特性。

## <a name="syntax"></a>语法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>参数

*value*<br/>
描述指针类型的值： **ptr**， **ref**，或**唯一**。

## <a name="remarks"></a>备注

**Pointer_default** c + + 属性具有相同的功能[pointer_default](/windows/desktop/Midl/pointer-default) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[defaultvalue](defaultvalue.md)的示例使用**pointer_default**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)  