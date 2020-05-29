---
title: DontUseNewUseMake 类
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371556"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>备注

防止在`new`中使用`RuntimeClass`运算符。 因此，您必须改用[Make 函数](make-function.md)。

## <a name="members"></a>成员

### <a name="public-operators"></a>公共运算符

名称                                             | 说明
------------------------------------------------ | ---------------------------------------------------------------------------
[不要使用新使用制作：：运算符新](#operator-new) | 重载运算符`new`并防止它在 中使用`RuntimeClass`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`DontUseNewUseMake`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>不要使用新使用制作：：运算符新

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>参数

*__unnamed0*<br/>
指定要分配的内存字节数的未命名参数。

*位置*<br/>
要分配的类型。

### <a name="return-value"></a>返回值

提供了一种在重载运算符时传递其他参数的方法`new`。

### <a name="remarks"></a>备注

重载运算符`new`并防止它在 中使用`RuntimeClass`。
