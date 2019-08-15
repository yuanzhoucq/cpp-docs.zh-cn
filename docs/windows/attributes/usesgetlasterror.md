---
title: usesgetlasterror (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: b14316bd929f4b41b13a76c41e94b31b7534e9d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513892"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

告诉调用方如果在调用该函数时出现错误, 则调用方可以调用`GetLastError`来检索错误代码。

## <a name="syntax"></a>语法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>备注

**Usesgetlasterror** C++特性具有与[usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**usesgetlasterror**的示例, 请参阅[idl_module](idl-module.md)示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**module**特性|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)