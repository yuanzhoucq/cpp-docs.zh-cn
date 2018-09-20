---
title: out_of_memory 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3da944d519964105bd43135d61b5874ad96a6670
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378810"
---
# <a name="outofmemory-class"></a>out_of_memory 类

一种方法将因系统或设备内存不足而失败时引发的异常。

## <a name="syntax"></a>语法

```
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[out_of_memory 构造函数](#ctor)|初始化 `out_of_memory` 类的新实例。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>要求

**标头：** amprt.h

**命名空间：** 并发
## <a name="ctor"></a> out_of_memory

初始化类的新实例。

### <a name="syntax"></a>语法

```
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误说明。

### <a name="return-value"></a>返回值

`out_of_memory` 类的新实例。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
