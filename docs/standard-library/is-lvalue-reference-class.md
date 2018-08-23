---
title: is_lvalue_reference 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d21fcc27b5b4f92b690d8fae7669a18a5fcc1c46
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964926"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference 类

测试类型是否是左值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>参数

*Ty*查询的类型。

## <a name="remarks"></a>备注

此类型谓词的实例保留为 true 如果类型*Ty*是对某个对象或函数，否则为 false 的引用。 请注意， *Ty*可能右值引用。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
