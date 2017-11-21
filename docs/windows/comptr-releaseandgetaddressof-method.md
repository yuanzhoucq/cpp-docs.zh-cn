---
title: "Comptr:: Releaseandgetaddressof 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs: C++
helpviewer_keywords: ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6711cc93071c1e260a5d216a6ad21add9c00540
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf 方法
释放与此 ComPtr 关联的接口，然后检索 [ptr_](../windows/comptr-ptr-data-member.md) 数据成员的地址，其中包含指向已释放接口的指针。  
  
## <a name="syntax"></a>语法  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>返回值  
 地址[ptr_](../windows/comptr-ptr-data-member.md)此 ComPtr 的数据成员。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)   
 [ComPtr::ptr_ 数据成员](../windows/comptr-ptr-data-member.md)