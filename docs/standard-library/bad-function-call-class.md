---
title: bad_function_call 类
ms.date: 11/04/2016
f1_keywords:
- functional/std::bad_function_call
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
ms.openlocfilehash: 6d0a3f5f5b6ac48d23b937b04b4521799ba31502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376388"
---
# <a name="badfunctioncall-class"></a>bad_function_call 类

报告错误的函数调用。

## <a name="syntax"></a>语法

```cpp
class bad_function_call : public std::exception {};
```

## <a name="remarks"></a>备注

该类描述引发的异常以指示在 [function 类](../standard-library/function-class.md)上调用 `operator()`
