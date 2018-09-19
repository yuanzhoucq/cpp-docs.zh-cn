---
title: is_trivially_default_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73bdd8186f2ce56e4a6ecec0fa4f9468d9da8e8c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102702"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 类

测试类型是否具有普通默认构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有普通构造函数，否则为 false 的类。

一个类的默认构造函数*Ty*并不重要如果：

- 它是一个隐式声明的默认构造函数

- 该类*Ty*不具有虚拟函数

- 该类*Ty*不具有虚拟基

- 类的所有直接都基均*Ty*具有普通构造函数

- 类类型的所有非静态数据成员的类具有普通构造函数

- 类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
