---
title: 'Handlenulltraits:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 155fb5a07f747e4107e630b0db65d321ee726e2c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602211"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close 方法

关闭指定的句柄。

## <a name="syntax"></a>语法

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*h*  
要关闭的句柄。

## <a name="return-value"></a>返回值

**true**如果处理*h*关闭成功; 否则为**false**。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[HANDLENullTraits 结构](../windows/handlenulltraits-structure.md)