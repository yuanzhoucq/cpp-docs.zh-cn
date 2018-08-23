---
title: 'Activationfactory:: Queryinterface 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 2a9b71aa-61c0-43f7-aa35-00f0ee0af031
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8783d30aa018e0b29705c4c6bdda3b9e2a47af4a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613227"
---
# <a name="activationfactoryqueryinterface-method"></a>ActivationFactory::QueryInterface 方法

检索指向指定接口的指针。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>参数

*riid*  
接口 ID。

*ppvObject*  
完成此操作后，指向由参数指定的接口的指针*riid*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ActivationFactory 类](../windows/activationfactory-class.md)