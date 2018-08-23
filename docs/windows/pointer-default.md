---
title: pointer_default |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 391b30251235fdd15ec1e96304e956740cb58f1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610143"
---
# <a name="pointerdefault"></a>pointer_default

指定所有指针，除顶级指针在参数列表中显示的默认指针特性。

## <a name="syntax"></a>语法

```cpp
[ pointer_default(
   value
) ]
```

### <a name="parameters"></a>参数

*value*  
描述指针类型的值： **ptr**， **ref**，或**唯一**。

## <a name="remarks"></a>备注

**Pointer_default** c + + 属性具有相同的功能[pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[defaultvalue](../windows/defaultvalue.md)的示例使用**pointer_default**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[接口特性](../windows/interface-attributes.md)  