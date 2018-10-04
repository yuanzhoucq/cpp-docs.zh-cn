---
title: 在 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31c47fa07375c587257bc979ac68b64381880398
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790342"
---
# <a name="in-c"></a>in (C++)

指示参数是要从调用过程传递给被调用过程。

## <a name="syntax"></a>语法

```cpp
[in]
```

## <a name="remarks"></a>备注

**中**c + + 属性具有相同的功能[中](/windows/desktop/Midl/in)MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](bindable.md)有关如何使用的示例**中**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**retval**|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)  