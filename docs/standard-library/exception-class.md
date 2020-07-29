---
title: exception 类
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: fd3fb3c48e9501b7aaf90bca14ea98530b245ec0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228266"
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

具体而言，此基类是中定义的标准异常类的根 [\<stdexcept>](../standard-library/stdexcept.md) 。 默认构造函数将 `what` 返回的 C 字符串值保留为不指定，但是可以通过某些派生类的构造函数定义为由实现定义的 C 字符串。 无成员函数引发任何异常。

**`int`** 参数用于指定不应分配任何内存。 的值 **`int`** 被忽略。

> [!NOTE]
> 构造函数 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 C++ 标准库的 Microsoft 扩展。

## <a name="example"></a>示例

有关从类继承的标准异常类的用法的示例 `exception` ，请参见中定义的任何类 [\<stdexcept>](../standard-library/stdexcept.md) 。
