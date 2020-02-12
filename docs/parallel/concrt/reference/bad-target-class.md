---
title: bad_target 类
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142848"
---
# <a name="bad_target-class"></a>bad_target 类

此类描述消息块被给予指向目标的指针，但该目标对于正在执行的操作无效时引发的异常。

## <a name="syntax"></a>语法

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[bad_target](#ctor)|已重载。 构造 `bad_target` 对象。|

## <a name="remarks"></a>备注

通常会出于如下原因引发此异常：目标尝试使用为不同目标保留的消息，或释放不保存的保留项。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`bad_target`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="ctor"></a>bad_target

构造 `bad_target` 对象。

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
错误的描述性消息。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)
