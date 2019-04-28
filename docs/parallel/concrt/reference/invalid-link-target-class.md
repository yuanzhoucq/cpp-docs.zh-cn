---
title: invalid_link_target 类
ms.date: 11/04/2016
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
ms.openlocfilehash: 3ef34ab7607c444044b6dde17f3db3f73d0d7086
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205650"
---
# <a name="invalidlinktarget-class"></a>invalid_link_target 类

此类描述调用消息块的 `link_target` 方法且消息块无法链接到目标时引发的异常。 这可能是因为超出消息块允许的链接数或两次尝试将特定目标链接到同一源。

## <a name="syntax"></a>语法

```
class invalid_link_target : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_link_target](#ctor)|已重载。 构造 `invalid_link_target` 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_link_target`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_link_target

构造 `invalid_link_target` 对象。

```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)
