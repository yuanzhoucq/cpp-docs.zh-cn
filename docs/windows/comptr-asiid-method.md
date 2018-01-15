---
title: "Comptr:: Asiid 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::AsIID
dev_langs: C++
helpviewer_keywords: AsIID method
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e19a313da257d9aefce68a61d43278e22bf88bab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="comptrasiid-method"></a>ComPtr::AsIID 方法
返回表示由指定接口 ID 标识的接口的 ComPtr 对象。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 接口 ID。  
  
 `p`  
 如果支持，指向由指定的接口的双向间接指针`riid`参数; 否则为指向 IUnknown 的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="requirements"></a>惠?  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)