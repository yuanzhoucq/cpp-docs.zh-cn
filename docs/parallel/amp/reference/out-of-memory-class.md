---
title: out_of_memory 类
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336807"
---
# <a name="out_of_memory-class"></a>out_of_memory 类

当方法因缺少系统或设备内存而失败时引发的异常。

## <a name="syntax"></a>语法

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[out_of_memory构造函数](#ctor)|初始化 `out_of_memory` 类的新实例。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>要求

**标题：** amprt.h

**命名空间：** 并发

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

初始化此类的新实例。

### <a name="syntax"></a>语法

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
对错误的说明。

### <a name="return-value"></a>返回值

`out_of_memory` 类的新实例。

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
