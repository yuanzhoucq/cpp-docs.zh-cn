---
title: 'Platform:: recreateexception 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
dev_langs:
- C++
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28434f6c8c35f2cd4cfc15953f761d28037626e6
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109714"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException 方法

此方法仅供内部使用，不用于用户代码。 请改用 exception:: createexception 方法。

## <a name="syntax"></a>语法

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>参数

*hr*

### <a name="property-valuereturn-value"></a>属性值/返回值

基于指定的 HRESULT 返回新的 Platform::Exception^。
