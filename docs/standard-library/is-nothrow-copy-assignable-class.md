---
title: is_nothrow_copy_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47cfa4d49dce7f7503c9e707d3a2f8787b4f53a3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable 类

测试类型是否具有编译器已知不会引发的复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

## <a name="remarks"></a>备注

如果可引用类型 `T` 的 `is_nothrow_assignable<T&, const T&>` 为 true，则类型谓词的实例为 true；否则为 false。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable 类](../standard-library/is-nothrow-assignable-class.md)<br/>
