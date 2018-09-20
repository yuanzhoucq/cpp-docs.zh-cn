---
title: helpstringdll |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1eecedca8988c95466a3f257fbc77768b7c67b3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392861"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用于执行文档字符串查找 （本地化） DLL 的名称。

## <a name="syntax"></a>语法

```cpp
[ helpstringdll(
   "string"
) ]
```

### <a name="parameters"></a>参数

*string*<br/>
要用于执行文档字符串查找 DLL。

## <a name="remarks"></a>备注

**Helpstringdll** c + + 属性具有相同的功能[helpstringdll](/windows/desktop/Midl/helpstringdll) MIDL 特性。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**接口**，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[接口特性](../windows/interface-attributes.md)<br/>
[类特性](../windows/class-attributes.md)<br/>
[方法特性](../windows/method-attributes.md)  