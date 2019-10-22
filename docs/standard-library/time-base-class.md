---
title: time_base 类
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685784"
---
# <a name="time_base-class"></a>time_base 类

类用作类模板 time_get 的各个方面的基类，只定义枚举类型 `dateorder` 和此类型的几个常量。

## <a name="syntax"></a>语法

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>备注

每个常量以不同的方式对日期组件进行排序。 这些常量包括：

- `no_order` 指定无特定顺序。

- `dmy` 指定订单 day、month 和 year，如2月1979。

- `mdy` 指定订单 month，day，then year，如1979年12月2日。

- `ymd` 指定订单 year、month 和 day，如1979/12/2 中所示。

- `ydm` 指定订单 year、day、then 月份，如1979年12月。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
