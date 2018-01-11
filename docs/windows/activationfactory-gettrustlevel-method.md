---
title: "Activationfactory:: Gettrustlevel 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs: C++
helpviewer_keywords: GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48db1632c50726073372e314a338cdca543c29e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel 方法
获取当前 ActivationFactory 实例化的对象的信任级别。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### <a name="parameters"></a>参数  
 `trustLvl`  
 完成此操作后，ActivationFactory 实例化的运行时类的信任级别。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则将发出断言错误并将 `trustLvl` 设置为 FullTrust。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)