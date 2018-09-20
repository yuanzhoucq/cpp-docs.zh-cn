---
title: 'Semaphore:: operator = 运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b35268cd883245b125aa7c87919124b29451ff1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420317"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= 运算符

将从指定句柄**信号量**对象与当前**信号量**对象。

## <a name="syntax"></a>语法

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>参数

*h*<br/>
对右值引用**信号量**对象。

## <a name="return-value"></a>返回值

对当前的引用**信号量**对象。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Semaphore 类](../windows/semaphore-class.md)