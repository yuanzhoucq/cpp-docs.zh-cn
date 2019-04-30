---
title: bad_exception 类
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 94d1104b66fc6bd84e209caa23ce309cffd9fa85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377812"
---
# <a name="badexception-class"></a>bad_exception 类

该类描述可从意外处理程序引发的异常。

## <a name="syntax"></a>语法

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>备注

如果 `bad_exception` 包含在函数的引发列表中，则 [unexpected](../standard-library/exception-functions.md#unexpected) 将引发 `bad_exception`，而不是终止或调用使用 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 指定的其他函数。

返回的值`what`是实现定义的 C 字符串。 无成员函数引发任何异常。

有关通过 `bad_exception` 类继承的成员列表，请参阅 [exception 类](../standard-library/exception-class.md)。

## <a name="example"></a>示例

有关引发 `bad_exception` 的 [unexpected](../standard-library/exception-functions.md#unexpected) 的使用示例，请参阅 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。

## <a name="requirements"></a>要求

**标头：**\<exception>

**命名空间：** std

## <a name="see-also"></a>请参阅

[exception 类](../standard-library/exception-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
