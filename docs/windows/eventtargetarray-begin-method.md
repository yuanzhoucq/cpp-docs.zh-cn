---
title: "Eventtargetarray:: Begin 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs: C++
helpviewer_keywords: Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 092aa684cace186e3aa5ad443e6f419f10d68160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
ComPtr<IUnknown>* Begin();  
```  
  
## <a name="return-value"></a>返回值  
 事件处理程序在内部数组的第一个元素的地址。  
  
## <a name="remarks"></a>备注  
 获取事件处理程序在内部数组的第一个元素的地址。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)