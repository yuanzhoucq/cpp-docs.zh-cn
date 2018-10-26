---
title: idl_quote （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31e06d83ce64675b5b1e8ac9cbb865bfb3eff334
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074158"
---
# <a name="idlquote"></a>idl_quote

可以使用不支持当前版本的 Visual c + + 中的 IDL 构造并将它们传递到生成的.idl 文件。

## <a name="syntax"></a>语法

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>参数

*文本*<br/>
希望 Visual c + + 编译器，而不返回编译器错误传递给生成的.idl 文件的属性名称。

## <a name="remarks"></a>备注

如果**idl_quote** c + + 属性使用的独立特性 （与右括号后面的分号），然后*文本*原样合并的.idl 文件中放置。 如果**idl_quote**使用的符号*文本*放在该符号的属性块内。

## <a name="example"></a>示例

下面的代码演示如何可以指定不支持的属性 (使用**在**，这受支持) 以及如何定义和使用未定义的.idl 构造：

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

此代码会导致`MYFLOT`并`MYDUB`并*文本*要置于生成的.idl 文件中的项。 *名称*参数将强制*文本*在引用的任何操作之前放置*名称*生成的.idl 文件中。 *依赖项*参数强制依赖关系列表定义之前放置*文本*生成的.idl 文件中。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)