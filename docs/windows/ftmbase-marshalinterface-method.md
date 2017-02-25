---
title: "FtmBase::MarshalInterface 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::MarshalInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MarshalInterface 方法"
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::MarshalInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

写入流中需要数据的初始化放到某客户端进程的代理对象。  
  
## 语法  
  
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
  
#### 参数  
 `pStm`  
 对在封送处理期间将使用流的指针。  
  
 `riid`  
 解封送对的接口标识符的引用。  必须从接口派生 IUnknown 此接口。  
  
 `pv`  
 要封送处理的接口指针的指针；，如果调用方不具有指向所需接口，可以为空。  
  
 `dwDestContext`  
 指定接口将封送对象的上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 目前， 分离收处理会出现在当前进程中 \(MSHCTX\_INPROC\) 的另一个单元或在计算机上其他进程和当前进程 \(MSHCTX\_LOCAL\) 相同。  
  
 `pvDestContext`  
 留待将来使用；必须为零。  
  
 `mshlflags`  
 标志指示封送的数据都将传输回客户端进程 \- 的典型情况或写入全局表，它可能由多客户端检索。  
  
## 返回值  
 S\_OK  
 接口指针封送。成功  
  
 E\_NOINTERFACE  
 不支持指定的接口。  
  
 STG\_E\_MEDIUMFULL  
 流已满。  
  
 E\_FAIL  
 操作失败。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)