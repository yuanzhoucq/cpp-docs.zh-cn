---
title: "Chaininterfaces:: Cancastto 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f614ec0eff2b448c8f20c88557f6228f85a770bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo 方法
指示指定的接口 ID 是否可以强制转换为每个非默认模板参数定义专用化。  
  
## <a name="syntax"></a>语法  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 接口 ID。  
  
 `ppv`  
 指向成功强制转换的最后一个接口 ID 的指针。  
  
## <a name="return-value"></a>返回值  
 `true`如果所有强制转换操作成功，则否则为`false`。  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)