---
title: "Comptr:: Detach 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::Detach
dev_langs: C++
helpviewer_keywords: Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: feb76819ce032608fdc717b3176f0242149eb8a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrdetach-method"></a>ComPtr::Detach 方法
解除关联这`ComPtr`从它所表示的接口的对象。  
  
## <a name="syntax"></a>语法  
  
```  
T* Detach();  
```  
  
## <a name="return-value"></a>返回值  
 指向由这表示的接口的指针`ComPtr`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)