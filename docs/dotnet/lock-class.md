---
title: lock 类
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 8876810b15a7d2736f2c8ab0ca1f4c6011918a5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547129"
---
# <a name="lock-class"></a>lock 类

此类会自动执行同步的对象的访问，从多个线程的锁。  在构造时获取该锁和销毁它的版本时锁定。

## <a name="syntax"></a>语法

```
ref class lock;
```

## <a name="remarks"></a>备注

`lock` 仅适用于 CLR 对象并且仅可以使用 CLR 代码中。

在内部，此锁类使用<xref:System.Threading.Monitor>的访问进行同步。 在同步，请参阅此主题的更多详细信息。

## <a name="requirements"></a>要求

**标头文件** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[lock](../dotnet/lock.md)<br/>
[lock 成员](../dotnet/lock-members.md)