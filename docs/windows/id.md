---
title: id |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b7ac87241e9089cc8c0152a6d0c3966dc32fa08
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600237"
---
# <a name="id"></a>id

指定*dispid* （属性或方法，请在接口或调度接口） 的成员函数的参数。

## <a name="syntax"></a>语法

```cpp
[ id(
   dispid
) ]
```

### <a name="parameters"></a>参数

*dispid*  
接口方法的调度 ID。

## <a name="remarks"></a>备注

**Id** c + + 属性具有相同的功能[id](http://msdn.microsoft.com/library/windows/desktop/aa367040) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](../windows/bindable.md)有关如何使用的示例**id**。

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

[IDL 特性](../windows/idl-attributes.md)  
[方法特性](../windows/method-attributes.md)  
[数据成员特性](../windows/data-member-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[in](../windows/in-cpp.md)  
[out](../windows/out-cpp.md)  