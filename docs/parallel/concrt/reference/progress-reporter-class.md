---
title: progress_reporter 类
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: dac74085278418153ddec502f6257ce13885704d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282534"
---
# <a name="progressreporter-class"></a>progress_reporter 类

进度报告器类允许报告特定类型的进度通知。 每个 progress_reporter 对象都是绑定到特定异步动作或操作的。

## <a name="syntax"></a>语法

```
template<typename _ProgressType>
class progress_reporter;
```

#### <a name="parameters"></a>参数

*_ProgressType*<br/>
通过进度报告器报告的每个进度通知的负载类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[report](#report)|向进度报告器绑定到的异步动作或操作发送进度报告。|

## <a name="remarks"></a>备注

此类型是仅适用于 Windows 运行时应用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`progress_reporter`

## <a name="requirements"></a>要求

**标头：** ppltasks.h

**命名空间：** 并发

##  <a name="ctor"></a> progress_reporter

```
progress_reporter();
```

##  <a name="report"></a> 报表

向进度报告器绑定到的异步动作或操作发送进度报告。

```
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>参数

*val*<br/>
要通过进程通知报告的负载。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)
