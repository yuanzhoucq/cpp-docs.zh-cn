---
title: 'Hstring:: Attach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
dev_langs:
- C++
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2f0a9116e9abe07628d2b205bd5249d9354d6f88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413908"
---
# <a name="hstringattach-method"></a>HString::Attach 方法

将指定相关联**HString**对象与当前**HString**对象。

## <a name="syntax"></a>语法

```cpp
void Attach(
       HSTRING hstr
       ) throw()  
```

### <a name="parameters"></a>参数

*hstr*<br/>
将现有**HString**对象。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)