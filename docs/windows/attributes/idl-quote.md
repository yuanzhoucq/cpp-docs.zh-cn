---
title: idl_quote （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168024"
---
# <a name="idl_quote"></a>idl_quote

允许你使用当前版本的视觉对象C++不支持的 IDL 构造，并将其传递到生成的 .idl 文件。

## <a name="syntax"></a>语法

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>parameters

*text*<br/>
您希望 Microsoft C++编译器传递到生成的 .idl 文件的属性名称，但不会返回编译器错误。

## <a name="remarks"></a>备注

如果**idl_quote** C++特性用作独立特性（在右括号后带有分号），则*文本*将按原样放置在合并的 .idl 文件中。 如果在符号上使用**idl_quote** ，则将*文本*置于该符号的特性块内。

## <a name="example"></a>示例

下面的代码演示如何指定不支持的属性（在支持的**中**使用）以及如何定义和使用未定义的 .idl 构造：

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

此代码会导致在生成的 .idl 文件中放置 `MYFLOT` 和 `MYDUB` 以及*文本*项。 *Name*参数强制在生成的 .idl 文件中引用*名称*的任何内容之前放置*文本*。 *依赖项*参数强制在生成的 .idl 文件中的*文本*前放置依赖项列表定义。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)
