---
title: 'Safeint:: Safeint |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de318ab79638f63fae98856987340ad62534f695
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721340"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt

构造**SafeInt**对象。

## <a name="syntax"></a>语法

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)  
```

### <a name="parameters"></a>参数

*i*<br/>
[in]新的值**SafeInt**对象。 这必须是类型 T 或 U，具体取决于构造函数的参数。

*b*<br/>
[in]新的布尔值**SafeInt**对象。

*u*<br/>
[in]一个**SafeInt**为类型 u。新**SafeInt**对象将具有相同的值*u*，但将类型为 t。

U 中存储的数据类型**SafeInt**。 这可以是一个布尔值、 字符或整数类型。 如果它是整数类型，可以对其签名或未签名且长度在 8 到 64 位之间。

## <a name="remarks"></a>备注

有关模板类型的详细信息`T`并`E`，请参阅[SafeInt 类](../windows/safeint-class.md)。

构造函数中，输入的参数*我*或*u*，必须为布尔值、 字符或整数类型。 如果它是另一种类型的参数， **SafeInt**类将调用[static_assert](../cpp/static-assert.md)以指示输入的参数无效。

使用模板类型的构造函数`U`自动将输入的参数转换为指定的类型`T`。 **SafeInt**类将转换数据，而不丢失任何数据。 它报告给错误处理程序`E`不能转换为类型的数据如果`T`无数据丢失。

如果您创建**SafeInt**布尔参数，则需立即初始化的值。 无法构造**SafeInt**使用代码`SafeInt<bool> sb;`。 这将生成编译错误。

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** msl:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 库](../windows/safeint-library.md)  
[SafeInt 类](../windows/safeint-class.md)  
[SafeIntException 类](../windows/safeintexception-class.md)