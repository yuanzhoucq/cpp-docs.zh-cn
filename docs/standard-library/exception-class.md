---
title: exception 类
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 009ef74d810976eb9f054b45e388ceb0fe612b2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400612"
---
# <a name="exception-class"></a>exception 类

该类用作某些表达式和 C++ 标准库所引发的所有异常的基类。

## <a name="syntax"></a>语法

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>备注

具体来说，此基类是 [\<stdexcept>](../standard-library/stdexcept.md) 中定义的标准异常类的根。 默认构造函数将 `what` 返回的 C 字符串值保留为不指定，但是可以通过某些派生类的构造函数定义为由实现定义的 C 字符串。 无成员函数引发任何异常。

**Int**参数，可指定应分配任何内存。 值**int**将被忽略。

> [!NOTE]
> 构造函数 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 C++ 标准库的 Microsoft 扩展。

## <a name="example"></a>示例

有关从 `exception` 类继承的标准异常类的使用示例，请参阅 [\<stdexcept>](../standard-library/stdexcept.md) 中定义的任意一个类。

## <a name="requirements"></a>要求

**标头：**\<exception>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
