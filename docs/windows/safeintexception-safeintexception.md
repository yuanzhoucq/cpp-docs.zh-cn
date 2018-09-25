---
title: 'Safeintexception:: Safeintexception |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24138db5ab772990f050fc8fcb6e5dad640a662d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396774"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException

创建**SafeIntException**对象。

## <a name="syntax"></a>语法

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>参数

*代码*<br/>
[in]一个枚举的数据值，描述发生的错误。

## <a name="remarks"></a>备注

可能的值*代码*文件 Safeint.h 中定义。 为方便起见，还此处列出可能的值。

- `SafeIntNoError`

- `SafeIntArithmeticOverflow`

- `SafeIntDivideByZero`

## <a name="requirements"></a>要求

**标头：** safeint.h

**Namespace:** msl:: utilities

## <a name="see-also"></a>请参阅

[SafeInt 库](../windows/safeint-library.md)<br/>
[SafeIntException 类](../windows/safeintexception-class.md)<br/>
[SafeInt 类](../windows/safeint-class.md)