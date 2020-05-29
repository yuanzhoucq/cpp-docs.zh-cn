---
title: sequenced_policy 类
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444914"
---
# <a name="sequenced_policy-class"></a>sequenced_policy 类

用作消除并行算法重载的唯一类型，并要求并行算法的执行不会并行化。

## <a name="syntax"></a>语法

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>备注

在使用 `execution::sequenced_policy` 策略执行并行算法期间，如果通过未捕获的异常退出元素访问函数，则应调用 `terminate()`。
