---
title: odl |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.odl
dev_langs:
- C++
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f376c2294dde0cc2fe538d3896aa28a9d136627
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221038"
---
# <a name="odl"></a>odl

标识为对象描述语言 (ODL) 接口的接口。 MIDL 编译器不需要**odl**属性; 仅为与较旧的.odl 文件的兼容性而识别它。

## <a name="syntax"></a>语法

```cpp
[odl]
```

## <a name="remarks"></a>备注

**Odl** c + + 属性具有相同的功能[odl](/windows/desktop/Midl/odl) MIDL 特性。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

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