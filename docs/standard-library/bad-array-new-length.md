---
title: bad_array_new_length 类
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: c4f4f58f7b28960bbacf695a675fbe4f20a54192
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443700"
---
# <a name="bad_array_new_length-class"></a>bad_array_new_length 类

类描述引发的异常，以指示分配请求未成功，因为数组大小小于零或大于其限制。

## <a name="syntax"></a>语法

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>备注

`what` 返回的值是实现定义的 C 字符串。 无成员函数引发任何异常。

## <a name="requirements"></a>要求

**标头：** \<新建 >

## <a name="see-also"></a>另请参阅

[Exception 类](../standard-library/exception-class.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
