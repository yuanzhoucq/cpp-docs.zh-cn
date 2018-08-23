---
title: importidl |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9bb6c1bd23eaf705f6ceb57e5fc4ea3354c0ddfc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42571353"
---
# <a name="importidl"></a>importidl

将指定的.idl 文件插入到生成的.idl 文件。

## <a name="syntax"></a>语法

```cpp
[ importidl(
   idl_file
) ];
```

### <a name="parameters"></a>参数

*idl_file*  
标识你想要将与你的应用程序将生成的.idl 文件合并的.idl 文件的名称。

## <a name="remarks"></a>备注

**Importidl** c + + 属性会放置在库块之外的部分 (在*idl_file*) 到您的程序生成的.idl 文件和库部分 (在*idl_file*) 到库的应用程序的部分生成的.idl 文件。

您可能想要使用**importidl**，例如，如果你想要生成的.idl 文件中使用手工编码.idl 文件。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
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

[编译器特性](../windows/compiler-attributes.md)  
[独立特性](../windows/stand-alone-attributes.md)  
[import](../windows/import.md)  
[importlib](../windows/importlib.md)  
[include](../windows/include-cpp.md)  
[includelib](../windows/includelib-cpp.md)  