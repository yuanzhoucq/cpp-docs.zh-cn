---
title: '&lt;操作&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3b0ccd540c56500c2f265aa6192a12fc2d5078b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457969"
---
# <a name="ltexecutiongt"></a>&lt;操作&gt;

介绍并行算法的执行策略。

## <a name="syntax"></a>语法

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```
### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[is_execution_policy 结构](is-execution-policy-struct.md)|检测执行策略, 以排除其他不明确的重载决策参与的函数签名。|
|[parallel_policy 类](parallel-policy-class.md)|用作消除并行算法重载的唯一类型, 并指示并行算法的执行可能会并行化。|
|[parallel_unsequenced_policy 类](parallel-unsequenced-policy-class.md)|用作消除并行算法重载的唯一类型, 并指示并行算法的执行可能会并行化并向量化。|
|[sequenced_policy 类](sequenced-policy-class.md)|用作消除并行算法重载的唯一类型, 并要求并行算法的执行不会并行化。|

## <a name="requirements"></a>要求

**标头:** \<执行 >

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[头文件引用](cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](cpp-standard-library-reference.md)
