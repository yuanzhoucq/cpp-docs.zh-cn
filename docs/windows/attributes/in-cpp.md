---
title: in （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: e97008d0399764beeca73dbbc5914e4b891df748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514603"
---
# <a name="in-c"></a>in (C++)

指示参数将从调用过程传递给被调用过程。

## <a name="syntax"></a>语法

```cpp
[in]
```

## <a name="remarks"></a>备注

**In** C++特性具有[与 MIDL 特性相同的功能](/windows/win32/Midl/in)。

## <a name="example"></a>示例

有关如何**在中**使用的示例，请参阅可[绑定](bindable.md)。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|Interface 参数，interface 方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|**retval**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)