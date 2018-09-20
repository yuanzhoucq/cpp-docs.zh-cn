---
title: lock 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380290"
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