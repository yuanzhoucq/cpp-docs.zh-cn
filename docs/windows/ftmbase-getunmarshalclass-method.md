---
title: "FtmBase::GetUnmarshalClass 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUnmarshalClass 方法"
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::GetUnmarshalClass 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取 COM 用于定位包含对应的代理代码的 DLL 的 CLSID。  COM 加载此 DLL 创建代理未初始化的实例的。  
  
## 语法  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### 参数  
 `riid`  
 解封送对的接口标识符的引用。  
  
 `pv`  
 要封送处理的接口指针的指针；如果调用方不具有指向所需接口，可以为空。  
  
 `dwDestContext`  
 指定接口将封送对象的上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 目前，分离收处理会出现在当前进程中 \(MSHCTX\_INPROC\) 的另一个单元或在计算机上其他进程和当前进程 \(MSHCTX\_LOCAL\) 相同。  
  
 `pvDestContext`  
 留待将来使用；必须为NULL。  
  
 `mshlflags`  
 如果此操作已完成，将使用的 CLSID 的指针在客户进程的代理。  
  
 `pCid`  
  
## 返回值  
 如果成功，则为 S\_OK；否则为 S\_FALSE。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)