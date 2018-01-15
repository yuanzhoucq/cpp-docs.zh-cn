---
title: "Ftmbase:: Marshalinterface 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs: C++
helpviewer_keywords: MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9df1e5d7559b434c1af0f1feff3b73b8141a8865
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface 方法
初始化代理对象某些客户端过程中的所需的数据将写入流。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### <a name="parameters"></a>参数  
 `pStm`  
 指向要封送处理期间使用的流指针。  
  
 `riid`  
 对要封送的接口标识符的引用。 此接口必须派生自 IUnknown 接口。  
  
 `pv`  
 指向要封送处理; 的接口指针如果调用方不具有到所需的接口指针，则可以为 NULL。  
  
 `dwDestContext`  
 其中将是取消封送指定的接口的目标上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 在当前进程 (MSHCTX_INPROC) 的另一单元，或者在当前进程 (MSHCTX_LOCAL) 所在的计算机上的另一个进程中，会发生取消封送。  
  
 `pvDestContext`  
 留待将来使用；必须为零。  
  
 `mshlflags`  
 指定是否要封送处理数据的传输回客户端进程-典型用例 — 或写入全局表，其中它可以通过多个客户端检索。  
  
## <a name="return-value"></a>返回值  
 S_OK  
 已成功封送的接口指针。  
  
 E_NOINTERFACE  
 不支持指定的接口。  
  
 STG_E_MEDIUMFULL  
 流已满。  
  
 E_FAIL  
 操作失败。  
  
## <a name="requirements"></a>惠?  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)