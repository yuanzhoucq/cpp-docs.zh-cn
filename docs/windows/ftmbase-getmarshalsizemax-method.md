---
title: "Ftmbase:: Getmarshalsizemax 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs: C++
helpviewer_keywords: GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d68889531c270db190f861eb20a34783b88987f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax 方法
获取上的封送指定的接口指针上指定的对象所需的字节数的上限。  
  
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
  
#### <a name="parameters"></a>参数  
 `riid`  
 对要封送的接口标识符的引用。  
  
 `pv`  
 要封送处理; 的接口指针可以为 NULL。  
  
 `dwDestContext`  
 其中将是取消封送指定的接口的目标上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 目前，取消封送可以发生在当前进程 (MSHCTX_INPROC) 的另一单元或在当前进程 (MSHCTX_LOCAL) 所在的计算机上的另一个进程中。  
  
 `pvDestContext`  
 留待将来使用;必须为 NULL。  
  
 `mshlflags`  
 标志，该值指示是否要封送数据的传输回客户端进程-典型用例 — 或写入全局表，其中它可以通过多个客户端检索。 指定一个或多个 MSHLFLAGS 枚举值。  
  
 `pSize`  
 此操作完成后，指向要写入到封送处理流的数据量上限。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为 E_FAIL 或 E_NOINTERFACE。  
  
## <a name="requirements"></a>惠?  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)