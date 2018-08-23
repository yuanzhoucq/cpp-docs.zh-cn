---
title: once_flag 结构 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 4275b99ada0dbfe1c974446d21862f7fa73aab38
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964491"
---
# <a name="onceflag-structure"></a>once_flag 结构

表示**struct**模板函数一起使用[call_once](../standard-library/mutex-functions.md#call_once)以确保初始化代码调用一次，即使出现多个执行线程。

## <a name="syntax"></a>语法

struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };

## <a name="remarks"></a>备注

`once_flag` **结构**只有一个默认构造函数。

可以创建 `once_flag` 类型的对象，但不能复制它们。

## <a name="requirements"></a>要求

**标头：** \<互斥体 >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
