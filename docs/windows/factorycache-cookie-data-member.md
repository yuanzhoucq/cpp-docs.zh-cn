---
title: "Factorycache:: Cookie 数据成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::FactoryCache::cookie
dev_langs: C++
helpviewer_keywords: cookie data member
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3cca7b708f7fc2a0fdaa5b975396958b967210a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="factorycachecookie-data-member"></a>FactoryCache::cookie 数据成员
支持的 Windows 运行时 c + + 模板库基础结构，不宜在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## <a name="remarks"></a>备注  
 包含一个值，用于标识已注册的 Windows 运行时或 COM 类对象，以及更高版本用于注销对象。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [FactoryCache 结构](../windows/factorycache-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)