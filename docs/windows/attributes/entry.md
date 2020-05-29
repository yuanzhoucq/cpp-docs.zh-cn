---
title: 项（C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167090"
---
# <a name="entry"></a>entry

通过标识 DLL 中的入口点，在模块中指定导出的函数或常量。

## <a name="syntax"></a>语法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>parameters

*id*<br/>
入口点的 ID。

## <a name="remarks"></a>备注

**Entry** C++属性的功能与[entry](/windows/win32/Midl/entry) MIDL 属性相同。

## <a name="example"></a>示例

有关**条目**的示例用法，请参阅[idl_module](idl-module.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|`idl_module` 特性|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)
