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
ms.openlocfilehash: 6bbaa215335a299eee8971b113fdcf3860e9b740
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106491"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 类

测试类型是否是右值引用。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

此类型谓词的实例保留为 true 如果类型*Ty*是[右值引用](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
