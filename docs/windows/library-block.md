---
title: library_block |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39067dd242fece7abb284448104115ac9a5ce4fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404366"
---
# <a name="libraryblock"></a>library_block

将放置在 IDL 库块中的构造。

## <a name="syntax"></a>语法

```cpp
[library_block]
```

## <a name="remarks"></a>备注

在将库块中的构造，您确保，它将传递到类型库，而不考虑是否引用。 默认情况下，唯一的构造修改[组件类](../windows/coclass.md)， [dispinterface](../windows/dispinterface.md)，并[idl_module](../windows/idl-module.md)属性放置在库块。

## <a name="example"></a>示例

在下面的代码中，自定义接口置于库块。

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[编译器特性](../windows/compiler-attributes.md)<br/>
[独立特性](../windows/stand-alone-attributes.md)  