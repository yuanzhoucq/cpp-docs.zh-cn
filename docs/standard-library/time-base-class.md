---
title: time_base 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1111ede44edc36e5399d82b3c4e088b20cc1c9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957293"
---
# <a name="timebase-class"></a>time_base 类

此类用作定义枚举的类型的模板类 time_get 的 facet 基类`dateorder`和此类型的多个常量。

## <a name="syntax"></a>语法

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```

## <a name="remarks"></a>备注

每个常量以不同的方式对日期组件进行排序。 这些常量包括：

- `no_order` 指定没有特定的顺序。

- `dmy` 指定顺序为日月，月，然后如下所示 2 年 12 月 1979 年。

- `mdy` 指定订购月份，一天，然后如下所示年 12 月 2 号，1979 年。

- `ymd` 指定订购年，月，然后一天，如 1979年/12/2 中所示。

- `ydm` 指定订单的年份，一天，然后如下所示 1979年: 2 年 12 月。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
