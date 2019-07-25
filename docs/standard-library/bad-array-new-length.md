---
title: bad_array_new_length 类
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459492"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length 类

类描述引发的异常, 以指示分配请求未成功, 因为数组大小小于零或大于其限制。

## <a name="syntax"></a>语法

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>备注

返回的值`what`是实现定义的 C 字符串。 无成员函数引发任何异常。

## <a name="requirements"></a>要求

**标头：** \<new>

## <a name="see-also"></a>请参阅

[exception 类](../standard-library/exception-class.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
