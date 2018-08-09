---
title: 'Ftmbase:: Unmarshalinterface 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a1991454daa76fcf7878a7487080124b5a34dbeb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644029"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface 方法
初始化新创建的代理，并对该代理返回的接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
### <a name="parameters"></a>参数  
 *pStm*  
 指向要取消封送的接口指针的流。  
  
 *riid*  
 为要取消封送的接口的标识符的引用。  
  
 *ppv*  
 此操作完成后，接收中请求的接口指针的指针变量的地址*riid*。 如果此操作成功，**ppv*包含要取消封送的接口的请求的接口指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为 E_NOINTERFACE 和 e_fail 两者之一。  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)