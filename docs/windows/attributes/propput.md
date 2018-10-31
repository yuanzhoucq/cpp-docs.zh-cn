---
title: propput （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9064a73dcafff8efbaffd50501dd86c2e91a29e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790559"
---
# <a name="propput"></a>propput

指定属性设置功能。

## <a name="syntax"></a>语法

```cpp
[propput]
```

## <a name="remarks"></a>备注

**Propput** c + + 属性具有相同的功能[propput](/windows/desktop/Midl/propput) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)的示例使用**propput**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`propget`, `propputref`|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)