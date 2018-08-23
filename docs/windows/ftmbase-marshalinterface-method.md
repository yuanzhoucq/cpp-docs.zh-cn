---
title: 'Ftmbase:: Marshalinterface 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a95521123a87a6ae68ce9f923779c1a6ceda4ccf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599706"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface 方法

初始化一些客户端进程中的代理对象所需的数据写入到流。

## <a name="syntax"></a>语法

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>参数

*pStm*  
指向要封送处理期间使用的流。

*riid*  
引用封送的接口标识符。 此接口必须派生自`IUnknown`接口。

*pv*  
要封送处理; 的接口指针的指针如果调用方不具有到所需的接口指针，则可以为 NULL。

*dwDestContext*  
其中将被取消封送指定的接口的目标上下文。

指定一个或多个 MSHCTX 枚举值。

在当前进程 (MSHCTX_INPROC) 的另一单元或者当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中，会发生取消封送。

*pvDestContext*  
留待将来使用；必须为零。

*mshlflags*  
指定要封送处理的数据是否传输回客户端进程 — 典型用例，或写入到全局表，其中可以由多个客户端检索它。

## <a name="return-value"></a>返回值

已成功地封送的接口指针，则为 S_OK。

E_NOINTERFACE 不支持指定的接口。

STG_E_MEDIUMFULL 流已满。

E_FAIL 操作失败。

## <a name="requirements"></a>要求

**标头：** ftm.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[FtmBase 类](../windows/ftmbase-class.md)