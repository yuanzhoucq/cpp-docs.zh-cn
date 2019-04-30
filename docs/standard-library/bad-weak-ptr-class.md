---
title: bad_weak_ptr 类
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: 78438ef3378e5002396eecb32b9b7a76d5b50325
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377486"
---
# <a name="badweakptr-class"></a>bad_weak_ptr 类

报告不良的 weak_ptr 异常。

## <a name="syntax"></a>语法

```cpp
class bad_weak_ptr : public std::exception
{
public:
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>备注

此类描述可从 [shared_ptr Class](../standard-library/shared-ptr-class.md) 构造函数引发的异常，该构造函数采用 [weak_ptr Class](../standard-library/weak-ptr-class.md) 类型的参数。 成员函数 `what` 返回 `"bad_weak_ptr"`。

## <a name="example"></a>示例

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="requirements"></a>要求

**标头：**\<memory>

**命名空间：** std

## <a name="see-also"></a>请参阅

[weak_ptr 类](../standard-library/weak-ptr-class.md)<br/>
