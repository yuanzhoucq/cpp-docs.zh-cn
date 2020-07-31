---
title: transmit_as （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.transmit_as
helpviewer_keywords:
- transmit_as attribute
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
ms.openlocfilehash: a34d57cc60dcc65e8b111c595fdd819dea407b78
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201123"
---
# <a name="transmit_as"></a>transmit_as

指示编译器将客户端和服务器应用程序操作的显示类型与传输类型相关联。

## <a name="syntax"></a>语法

```cpp
[ transmit_as(type) ]
```

### <a name="parameters"></a>参数

*type*<br/>
指定在客户端和服务器之间传输的数据类型。

## <a name="remarks"></a>备注

**Transmit_as** c + + 特性具有与[transmit_as](/windows/win32/Midl/transmit-as) MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何使用**transmit_as**特性：

```cpp
// cpp_attr_ref_transmit_as.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export] typedef struct _TREE_NODE_TYPE {
unsigned short data;
struct _TREE_NODE_TYPE * left;
struct _TREE_NODE_TYPE * right;
} TREE_NODE_TYPE;

[export] struct PACKED_NODE {
   unsigned short data;   // same as normal node
   int index;   // array index of parent
};

// A left node recursive built array of
// the nodes in the tree.  Can be unpacked with
// that knowledge
[export] typedef struct _TREE_XMIT_TYPE {
   int count;
   [size_is(count)] PACKED_NODE node[];
} TREE_XMIT_TYPE;

[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**`typedef`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[先导](export.md)
