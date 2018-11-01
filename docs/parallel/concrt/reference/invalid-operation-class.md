---
title: invalid_operation 类
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: 594c09ebedd2be55b288a7f31d55930244d80959
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473965"
---
# <a name="invalidoperation-class"></a>invalid_operation 类

此类描述执行无效操作时引发的异常，由并发运行时引发的其他异常类型不会对此异常进行更为准确的描述。

## <a name="syntax"></a>语法

```
class invalid_operation : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[invalid_operation](#ctor)|已重载。 构造 `invalid_operation` 对象。|

## <a name="remarks"></a>备注

引发此异常的各种方法通常会记录它们将引发此异常的环境。

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`invalid_operation`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="ctor"></a> invalid_operation

构造 `invalid_operation` 对象。

```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>参数

*消息 （_m)*<br/>
错误的描述性消息。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
