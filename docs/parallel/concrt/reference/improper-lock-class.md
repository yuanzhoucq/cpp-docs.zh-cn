---
title: improper_lock 类
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142399"
---
# <a name="improper_lock-class"></a>improper_lock 类

此类描述错误获取锁时引发的异常。

## <a name="syntax"></a>语法

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[improper_lock](#ctor)|已重载。 构造一个 `improper_lock exception`。|

## <a name="remarks"></a>备注

通常，当尝试在同一上下文中以递归方式获取非可重入锁时，将引发此异常。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`improper_lock`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>improper_lock

构造一个 `improper_lock exception`。

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[critical_section 类](critical-section-class.md)<br/>
[reader_writer_lock 类](reader-writer-lock-class.md)
