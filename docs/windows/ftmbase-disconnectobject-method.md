---
title: 'Ftmbase:: Disconnectobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b467162d2f5cc5b04bc43a6d31019eb08e17e750
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595401"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject 方法

强制释放对象的所有外部连接。 对象的服务器将调用此方法在关机前对象的实现。

## <a name="syntax"></a>语法

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>参数

*dwReserved*  
留待将来使用；必须为零。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="requirements"></a>要求

**标头：** ftm.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[FtmBase 类](../windows/ftmbase-class.md)