---
title: 'Comptr:: Get 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Get
dev_langs:
- C++
helpviewer_keywords:
- Get method
ms.assetid: 078eee51-7bca-4924-a74b-cd4f6a05de31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da8c4446d10f87514ec49feef95d05df2de721f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870723"
---
# <a name="comptrget-method"></a>ComPtr::Get 方法
检索指向与此 ComPtr 相关联的接口。  
  
## <a name="syntax"></a>语法  
  
```  
T* Get() const;  
```  
  
## <a name="return-value"></a>返回值  
 指向与此 ComPtr 相关联的接口指针。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)