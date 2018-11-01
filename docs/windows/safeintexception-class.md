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
ms.openlocfilehash: 80a1573c2f43b1f4b31731083974f87ba389fac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566655"
---
# <a name="safeintexception-class"></a>SafeIntException 类

`SafeInt`类使用`SafeIntException`以确定无法完成数学运算的原因。

> [!NOTE]
> 此库的最新版本位于[ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt)。

## <a name="syntax"></a>语法

```cpp
class SafeIntException;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                    | 描述
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | 创建一个 `SafeIntException` 对象。

## <a name="remarks"></a>备注

[SafeInt 类](../windows/safeint-class.md)是唯一使用的类`SafeIntException`类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SafeIntException`

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** msl:: utilities

## <a name="safeintexception"></a>Safeintexception:: Safeintexception

创建一个 `SafeIntException` 对象。

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>参数

*代码*<br/>
[in]一个枚举的数据值，描述发生的错误。

### <a name="remarks"></a>备注

可能的值*代码*文件 Safeint.h 中定义。 为方便起见，还此处列出可能的值。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
