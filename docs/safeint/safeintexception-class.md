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
ms.openlocfilehash: 2998bbb83fd568d7ff627d6598c32fb5b17c1e40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515562"
---
# <a name="safeintexception-class"></a>SafeIntException 类

`SafeInt` 类使用 `SafeIntException` 来确定数学运算为什么无法完成。

> [!NOTE]
> 有关此库的最新版本，请访问 [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)。

## <a name="syntax"></a>语法

```cpp
class SafeIntException;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

name                                                    | 说明
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | 创建一个 `SafeIntException` 对象。

## <a name="remarks"></a>备注

[SafeInt 类](../safeint/safeint-class.md)是唯一使用 `SafeIntException` 类的类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SafeIntException`

## <a name="requirements"></a>要求

**头：** safeint.h

**命名空间：** msl:: utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

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

文件 Safeint.h 中定义了 code 的可取值。 为了方便起见，此处还列出了可取值。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
