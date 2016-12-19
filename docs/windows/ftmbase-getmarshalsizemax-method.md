---
title: "FtmBase::GetMarshalSizeMax 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMarshalSizeMax 方法"
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::GetMarshalSizeMax 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取最大限制所需的字节数封送对指定对象指定的接口指针。  
  
## 语法  
  
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
  
#### 参数  
 `riid`  
 解封送对的接口标识符的引用。  
  
 `pv`  
 要封送的接口指针；可以为 NULL。  
  
 `dwDestContext`  
 指定接口将封送对象的上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 目前，分离收处理会出现在当前进程中 \(MSHCTX\_INPROC\) 的另一个单元或在计算机上其他进程和当前进程 \(MSHCTX\_LOCAL\) 相同。  
  
 `pvDestContext`  
 留待将来使用；必须为NULL。  
  
 `mshlflags`  
 标志指示封送的数据都将传输回客户端进程 \- 的典型情况 \(或写入全局表，它可能由多客户端检索。  指定一个或多个 MSHLFLAGS 枚举值。  
  
 `pSize`  
 该操作完成，到上限的指针上要写入的数据量为封送流。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_NOINTERFACE 或E\_FAIL 。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)