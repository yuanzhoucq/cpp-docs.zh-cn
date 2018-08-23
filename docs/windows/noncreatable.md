---
title: 不可创建 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a55daa9f8c742d847944ddb0459db208c7edf9cf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608119"
---
# <a name="noncreatable"></a>noncreatable

定义不能实例化本身的对象。

## <a name="syntax"></a>语法

```cpp
[noncreatable]
```

## <a name="remarks"></a>备注

**Noncreatable** c + + 属性具有相同的功能[不可创建](http://msdn.microsoft.com/library/windows/desktop/aa367118)MIDL 特性和自动传递到生成。由编译器的 IDL 文件。

当使用 ATL 的项目中使用此属性时，该属性的行为更改。 除了上述行为，该属性还注入[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏。 此宏对 ATL 指示不能从外部创建对象。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|**coclass**|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[类特性](../windows/class-attributes.md)  
