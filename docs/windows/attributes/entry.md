---
title: 条目 (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 703a55ee7c56b64a5b168016770508508bab09e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346135"
---
# <a name="entry"></a>entry

通过标识 DLL 中的入口点，在模块中指定的导出的函数或常量。

## <a name="syntax"></a>语法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>参数

*id*<br/>
入口点的 ID。

## <a name="remarks"></a>备注

**条目**C++属性具有相同的功能[条目](/windows/desktop/Midl/entry)MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[idl_module](idl-module.md)有关的示例用法**条目**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|`idl_module` 属性|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)