---
title: sequenced_policy 类
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 63be7166b84fa452f53baf6b6de16831eb657a23
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269189"
---
# <a name="sequencedpolicy-class"></a>sequenced_policy 类

作为一个唯一的类型用于区分重载的并行算法，并且需要并行算法的执行不可能会并行化。

## <a name="syntax"></a>语法

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>备注

使用并行算法的执行期间`execution::sequenced_policy`策略，如果未捕获的异常，通过退出元素访问函数的调用`terminate()`应被调用。
