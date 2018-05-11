---
title: defer_lock_t Structure | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::defer_lock_t
dev_langs:
- C++
ms.assetid: 4c4588eb-ca51-4949-b5d1-8539cc4577ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcf516c72d87b4d462d89e7dc6a58c351d4b37d6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="deferlockt-structure"></a>defer_lock_t 结构

表示一种类型，它定义 [defer_lock](../standard-library/mutex-functions.md#defer_lock) 对象以用于选择其中一个 [unique_lock](../standard-library/unique-lock-class.md) 的重载构造函数。

## <a name="syntax"></a>语法

```cpp
struct defer_lock_t;
```

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
