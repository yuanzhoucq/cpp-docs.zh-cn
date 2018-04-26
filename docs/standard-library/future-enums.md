---
title: '&lt;future&gt; 枚举 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: a32f777842b3c14a5c6f15d9c1c3b534bc4ffad8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 枚举

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[启动](#launch)|

## <a name="future_errc"></a>future_errc 枚举

为 [future_error](../standard-library/future-error-class.md) 类报告的所有错误提供符号名称。

class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };

## <a name="future_status"></a>future_status 枚举

为计时等待函数可返回的原因提供符号名称。

```cpp
enum future_status{    ready,
    timeout,
 deferred};
```

## <a name="launch"></a>launch 枚举

展示描述模板函数 [async](../standard-library/future-functions.md#async) 的可能模式的位掩码类型。

class launch{ async, deferred };

## <a name="see-also"></a>请参阅

[\<future>](../standard-library/future.md)<br/>
