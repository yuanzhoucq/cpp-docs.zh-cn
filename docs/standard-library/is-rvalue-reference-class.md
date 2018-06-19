---
title: is_rvalue_reference 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b8645e9ac8a8d3e8f40590105df234b4ef55bac
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857059"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 类

测试类型是否是右值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>参数

`Ty` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `Ty` 是[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)，则此类型谓词的实例为 true。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
