---
title: invalid_oversubscribe_operation 类
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 200743d41c1c45f2a957dba0716dd7aa07e3de76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405308"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation 类

此类描述时引发的异常`Context::Oversubscribe`与调用方法`_BeginOversubscription`参数设置为**false**而无需调用之前`Context::Oversubscribe`方法替换`_BeginOversubscription`参数设置为 **，则返回 true**。

## <a name="syntax"></a>语法

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|已重载。 构造 `invalid_oversubscribe_operation` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_oversubscribe_operation

构造 `invalid_oversubscribe_operation` 对象。

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
