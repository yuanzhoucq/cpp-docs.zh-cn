---
title: satype （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 708495d68b8cac4c49980e6a92b08e5ca9f37ff4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069992"
---
# <a name="satype"></a>satype

指定的数据类型`SAFEARRAY`结构。

## <a name="syntax"></a>语法

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>参数

*data_type*<br/>
数据类型为`SAFEARRAY`数据结构是作为参数传递给接口方法。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

## <a name="remarks"></a>备注

**Satype** c + + 属性指定的数据类型`SAFEARRAY`。

> [!NOTE]
> 从删除一定程度的间接性`SAFEARRAY`从它在.cpp 文件中的声明方式生成的.idl 文件中的指针。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[id](id.md)