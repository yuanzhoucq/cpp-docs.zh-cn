---
title: is_nothrow_copy_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e540d6fe4c00772af01b187d24efae18fd62357f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957553"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 类

测试类型是否具有编译器已知不会引发的复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>参数

*T*查询的类型。

## <a name="remarks"></a>备注

类型谓词的实例为 true 可引用类型*T*其中`is_nothrow_assignable<T&, const T&>`保存 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable 类](../standard-library/is-nothrow-assignable-class.md)<br/>
