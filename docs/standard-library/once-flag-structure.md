---
title: once_flag 结构 | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104330"
---
# <a name="onceflag-structure"></a>once_flag 结构

表示**struct**模板函数一起使用[call_once](../standard-library/mutex-functions.md#call_once)以确保初始化代码调用一次，即使出现多个执行线程。

## <a name="syntax"></a>语法

once_flag 结构 {constexpr once_flag() noexcept;};

## <a name="remarks"></a>备注

`once_flag` **结构**只有一个默认构造函数。

可以创建 `once_flag` 类型的对象，但不能复制它们。

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
