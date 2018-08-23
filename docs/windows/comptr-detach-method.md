---
title: 'Comptr:: Detach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84db0a82dfe6f9333f6a533aa9bc2bb529854fa2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593407"
---
# <a name="comptrdetach-method"></a>ComPtr::Detach 方法

取消关联这**ComPtr**从它所代表的接口的对象。

## <a name="syntax"></a>语法

```cpp
T* Detach();
```

## <a name="return-value"></a>返回值

指向表示此接口的指针**ComPtr**对象。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)