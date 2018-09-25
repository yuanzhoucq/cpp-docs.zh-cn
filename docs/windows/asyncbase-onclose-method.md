---
title: 'Asyncbase:: Onclose 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnClose
dev_langs:
- C++
helpviewer_keywords:
- OnClose method
ms.assetid: 96766450-c262-4611-8534-7d190b799142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 866e4a285a92fb7d80d0fe0d8240ebdda107de23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419383"
---
# <a name="asyncbaseonclose-method"></a>AsyncBase::OnClose 方法

当在派生类中重写，会关闭一个异步操作。

## <a name="syntax"></a>语法

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[AsyncBase 类](../windows/asyncbase-class.md)<br/>
[AsyncBase::Close 方法](../windows/asyncbase-close-method.md)