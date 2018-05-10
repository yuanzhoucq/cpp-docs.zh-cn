---
title: bad_function_call 类| Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e00dd485478a5a6fb7ff029afdad7bf7212fd56
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="badfunctioncall-class"></a>bad_function_call 类

报告错误的函数调用。

## <a name="syntax"></a>语法

```cpp
class bad_function_call
 : public std::exception {
 };
```

## <a name="remarks"></a>备注

该类描述引发的异常以指示在 [function 类](../standard-library/function-class.md)上调用 `operator()`
