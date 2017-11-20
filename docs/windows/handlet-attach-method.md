---
title: "Handlet:: Attach 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
dev_langs: C++
helpviewer_keywords: Attach method
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 572221b7232e25984d78ec903f8d13b9e08ba06b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="handletattach-method"></a>HandleT::Attach 方法
将指定的句柄与当前的 HandleT 对象相关联。  
  
## <a name="syntax"></a>语法  
  
```  
void Attach(  
   typename HandleTraits::Type h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 一个句柄。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
 [HandleT 类](../windows/handlet-class.md)