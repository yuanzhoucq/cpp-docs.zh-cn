---
title: 'Mutex:: mutex 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62a1fc796188c38dfbd3aff004eba15b7e30ea89
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600500"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex 构造函数

初始化的新实例**互斥体**类。

## <a name="syntax"></a>语法

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>参数

*h*  
句柄或右值引用的句柄，向**互斥体**对象。

## <a name="remarks"></a>备注

第一个构造函数初始化**互斥体**从指定句柄的对象。 第二个构造函数初始化**Mutex**对象从指定句柄，然后将 mutex 的所有权与当前**互斥体**对象。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅
[Mutex 类](../windows/mutex-class1.md)