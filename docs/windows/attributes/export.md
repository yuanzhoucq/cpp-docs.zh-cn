---
title: 导出 (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501605"
---
# <a name="export"></a>export

导致将数据结构放置在 .idl 文件中。

## <a name="syntax"></a>语法

```cpp
[export]
```

## <a name="remarks"></a>备注

**导出** C++特性会导致将数据结构放置在 .idl 文件中, 然后在类型库中以与二进制兼容的格式提供, 使其可用于任何语言。

即使该类只有公共成员 (等效于**结构**), 也不能将**导出**特性应用于类。

如果导出未命名的**枚举**或**结构**, 则会为其指定一个以 **__unnamed**<em>x</em>开头的名称, 其中*x*是一个序列号。

用于导出的 typedef 是基类型、结构、联合、枚举或类型标识符。  有关详细信息, 请参阅[typedef](/windows/win32/Midl/typedef) 。

## <a name="example"></a>示例

下面的代码演示如何使用**export**特性:

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**union**、 **typedef**、 **enum**、 **struct**或**interface**|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)