---
title: parallel_policy 类
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 7bb2b095a50e664dfc585e0bd4aaa608a6ad8e95
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268959"
---
# <a name="parallelpolicy-class"></a>parallel_policy 类

用作唯一类型可重载的并行算法来消除歧义，并指示并行算法的执行可能会并行化。

## <a name="syntax"></a>语法

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>备注

使用并行算法的执行期间`execution::parallel_policy`策略，如果未捕获的异常，通过退出元素访问函数的调用`terminate()`应被调用。
