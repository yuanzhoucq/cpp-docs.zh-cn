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
ms.openlocfilehash: c10a7f302b63c33869425c4e5bddb36a15373ea8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326554"
---
# <a name="improperlock-class"></a>improper_lock 类

此类描述错误获取锁时引发的异常。

## <a name="syntax"></a>语法

```
class improper_lock : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[improper_lock](#ctor)|已重载。 构造一个 `improper_lock exception`。|

## <a name="remarks"></a>备注

通常情况下，尝试获取相同的上下文上的非可重入锁以递归方式时，将引发此异常。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`improper_lock`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> improper_lock

构造一个 `improper_lock exception`。

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[critical_section 类](critical-section-class.md)<br/>
[reader_writer_lock 类](reader-writer-lock-class.md)
