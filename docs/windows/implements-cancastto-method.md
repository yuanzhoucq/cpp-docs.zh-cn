---
title: "Implements:: cancastto 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::CanCastTo
dev_langs: C++
helpviewer_keywords: CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 83d217cb749c350da45bcae2159e6b46d03f68cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo 方法
获取一个指向指定接口。  
  
## <a name="syntax"></a>语法  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 指接口 id。  
  
 `ppv`  
 如果成功，指向接口的指定`riid`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为指示错误，例如 E_NOINTERFACE 的 HRESULT。  
  
## <a name="remarks"></a>备注  
 这是一个内部帮助程序函数，执行 QueryInterface 操作。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Implements 结构](../windows/implements-structure.md)