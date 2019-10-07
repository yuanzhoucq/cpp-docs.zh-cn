---
title: bad_optional_access 类
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957103"
---
# <a name="bad_optional_access-class"></a>bad_optional_access 类

定义作为异常引发的对象的类型, 以报告尝试访问不包含值的`optional`对象的值时所发生的情况。

## <a name="syntax"></a>语法

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>请参阅

[\<可选 >](optional.md)\
[可选类](optional-class.md)
