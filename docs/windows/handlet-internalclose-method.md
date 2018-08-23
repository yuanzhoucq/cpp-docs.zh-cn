---
title: 'Handlet:: Internalclose 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc3f01227cb37285f11ef8256d0b101f156871b5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605511"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法

关闭当前**HandleT**对象。

## <a name="syntax"></a>语法

```cpp
virtual bool InternalClose();
```

## <a name="return-value"></a>返回值

**true**如果当前**HandleT**关闭成功; 否则为**false**。

## <a name="remarks"></a>备注

**InternalClose()** 是**受保护的**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HandleT 类](../windows/handlet-class.md)