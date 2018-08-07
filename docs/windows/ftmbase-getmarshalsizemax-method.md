---
title: 'Ftmbase:: Getmarshalsizemax 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c39c313f06bb4dd1f4dbc095df159a38625e9db8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570209"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax 方法
获取有关封送指定的接口指针上指定的对象所需的字节数的上限。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
### <a name="parameters"></a>参数  
 *riid*  
 引用封送的接口标识符。  
  
 *pv*  
 接口指针进行封送;可以为 NULL。  
  
 *dwDestContext*  
 其中将被取消封送指定的接口的目标上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 目前，取消封送可以发生在当前进程 (MSHCTX_INPROC) 的另一单元中或作为当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中。  
  
 *pvDestContext*  
 保留供将来使用;必须为 NULL。  
  
 *mshlflags*  
 标志，指示要封送处理的数据是否传输回客户端进程 — 典型用例，或写入到全局表，其中可以由多个客户端检索它。 指定一个或多个 MSHLFLAGS 枚举值。  
  
 *pSize*  
 此操作完成后，指向要写入到封送处理流的数据量上限。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为 E_FAIL 或 E_NOINTERFACE。  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)