---
title: "Ftmbase:: Unmarshalinterface 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs: C++
helpviewer_keywords: UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d4b4ba8230d9118c7de7624f957d8be47a24f81b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface 方法
初始化新创建的代理，并向该代理返回的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>参数  
 `pStm`  
 指向要取消封送的接口指针的流指针。  
  
 `riid`  
 为要取消封送的接口的标识符的引用。  
  
 `ppv`  
 此操作完成后，接收请求中的接口指针的指针变量的地址`riid`。 如果此操作成功，*`ppv`包含要取消封送的接口的请求的接口指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为 E_NOINTERFACE 或 E_FAIL。  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)