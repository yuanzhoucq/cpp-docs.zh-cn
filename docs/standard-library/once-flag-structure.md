---
title: once_flag 结构
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455198"
---
# <a name="onceflag-structure"></a>once_flag 结构

表示与模板函数[call_once](../standard-library/mutex-functions.md#call_once)一起使用的**结构**, 以确保只调用一次初始化代码, 即使存在多个执行线程。

## <a name="syntax"></a>语法

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>备注

该`once_flag` **结构**只有默认构造函数。

可以创建 `once_flag` 类型的对象，但不能复制它们。

## <a name="requirements"></a>要求

**标头:** \<mutex >

**命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
