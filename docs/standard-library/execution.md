---
title: '&lt;执行&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268419"
---
# <a name="ltexecutiongt"></a>&lt;执行&gt;

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
|[is_execution_policy 结构](is-execution-policy-struct.md)|检测到用于从否则为不明确的重载解析参与排除函数签名执行策略。|
|[parallel_policy 类](parallel-policy-class.md)|用作唯一类型可重载的并行算法来消除歧义，并指示并行算法的执行可能会并行化。|
|[parallel_unsequenced_policy 类](parallel-unsequenced-policy-class.md)|用作唯一类型可重载的并行算法来消除歧义，并指示可能会并行化且向量化并行算法的执行。|
|[sequenced_policy 类](sequenced-policy-class.md)|作为一个唯一的类型用于区分重载的并行算法，并且需要并行算法的执行不可能会并行化。|

## <a name="requirements"></a>要求

**标头：** \<执行 >

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[头文件引用](cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](cpp-standard-library-reference.md)
