---
title: make_exception_ptr 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ppltasks/std::make_exception_ptr
dev_langs:
- C++
ms.assetid: 8d81cf7a-818e-4b27-8d49-440ec3088609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 401bc3cd9933f44b92f5f361b1a1aaad24bc79ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436944"
---
# <a name="makeexceptionptr-function"></a>make_exception_ptr 函数

## <a name="syntax"></a>语法

```
template<class _E>
exception_ptr make_exception_ptr(_E _Except);
```

#### <a name="parameters"></a>参数

*_E*<br/>
异常类型。

*_Except*<br/>
异常值。

## <a name="return-value"></a>返回值

## <a name="requirements"></a>要求

**标头：** ppltasks.h

**命名空间：** std

## <a name="see-also"></a>请参阅

[std 命名空间](std-namespace.md)
