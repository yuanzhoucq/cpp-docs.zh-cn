---
title: retval (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 2a2865c1eda229f1a2fcd457c22119b2908c1caa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514043"
---
# <a name="retval"></a>retval

指定接收该成员的返回值的参数。

## <a name="syntax"></a>语法

```cpp
[retval]
```

## <a name="remarks"></a>备注

**Retval** C++特性具有与[retval](/windows/win32/Midl/retval) MIDL 特性相同的功能。

**retval**必须出现在函数声明中的最后一个参数上。

## <a name="example"></a>示例

有关**retval**的示例用法, 请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|Interface 参数, interface 方法|
|**可重复**|No|
|**必需的特性**|**out**|
|**无效的特性**|**in**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)