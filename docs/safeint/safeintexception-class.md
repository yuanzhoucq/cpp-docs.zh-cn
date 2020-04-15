---
title: SafeIntException 类
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349942"
---
# <a name="safeintexception-class"></a>SafeIntException 类

`SafeInt` 类使用 `SafeIntException` 来确定数学运算为什么无法完成。

> [!NOTE]
> 此库的最新版本位于[https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)。

## <a name="syntax"></a>语法

```cpp
class SafeIntException;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                    | 说明
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | 创建一个 `SafeIntException` 对象。

## <a name="remarks"></a>备注

[SafeInt 类](../safeint/safeint-class.md)是唯一使用 `SafeIntException` 类的类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SafeIntException`

## <a name="requirements"></a>要求

**头：** safeint.h

**命名空间：** msl:: utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>安全例外：安全例外

创建一个 `SafeIntException` 对象。

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>参数

*代码*<br/>
[输入] 描述所发生错误的枚举数据值。

### <a name="remarks"></a>备注

文件 Safeint.h 中定义了 code** 的可取值。 为了方便起见，此处还列出了可取值。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
