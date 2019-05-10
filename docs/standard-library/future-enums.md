---
title: '&lt;future&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 1e487128d4af5c6f9b3f29f5c71e52f616e1807a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159517"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 枚举

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[launch](#launch)|

## <a name="future_errc"></a>future_errc 枚举

为 [future_error](../standard-library/future-error-class.md) 类报告的所有错误提供符号名称。

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status"></a>future_status 枚举

为计时等待函数可返回的原因提供符号名称。

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch"></a>launch 枚举

展示描述模板函数 [async](../standard-library/future-functions.md#async) 的可能模式的位掩码类型。

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>请参阅

[\<future>](../standard-library/future.md)<br/>
