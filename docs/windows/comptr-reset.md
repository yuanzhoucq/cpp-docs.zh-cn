---
title: ComPtr::Reset |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86e7716ff4e9a0b4f5132abfd431a2649f22f80f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593088"
---
# <a name="comptrreset"></a>ComPtr::Reset

释放对与此相关联的接口指针的所有引用**ComPtr**。

## <a name="syntax"></a>语法

```cpp
unsigned long Reset();
```

## <a name="return-value"></a>返回值

已释放的引用的数量（如果存在）。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)