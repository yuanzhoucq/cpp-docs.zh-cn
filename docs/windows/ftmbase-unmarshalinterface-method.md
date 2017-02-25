---
title: "FtmBase::UnmarshalInterface 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase::UnmarshalInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnmarshalInterface 方法"
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase::UnmarshalInterface 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化新生成的代理接口并返回指向该代理。  
  
## 语法  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### 参数  
 `pStm`  
 对接口指针将封送流的指针。  
  
 `riid`  
 封送对的接口标识符的引用。  
  
 `ppv`  
 当完成此操作时，指针会指示接收接口指针变量的地址在 `riid`请求。  如果该操作成功，\*`ppv` 包含封送的接口请求接口指针。  
  
## 返回值  
 S\_OK，如果成功；否则，E\_NOINTERFACE 或 E\_FAIL。  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)