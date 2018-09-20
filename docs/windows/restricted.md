---
title: 受限 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b8de310f8abb3b417abbe96576d910513e25717
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398672"
---
# <a name="restricted"></a>restricted

指定不能任意调用模块、 接口或调度接口的成员。

## <a name="syntax"></a>语法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>参数

*interfaces*<br/>
可能不会调用任意 COM 对象的一个或多个接口。 此参数才有效时应用于类。

## <a name="remarks"></a>备注

**受限**c + + 属性具有相同的功能[受限](/windows/desktop/Midl/restricted)MIDL 特性。

## <a name="example"></a>示例

下面的代码演示如何使用**受限**属性：

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法，**接口**，**类**，**结构**|
|**可重复**|否|
|**必需的特性**|**组件类**(当应用于**类**或**结构**)|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[接口特性](../windows/interface-attributes.md)<br/>
[方法特性](../windows/method-attributes.md)  