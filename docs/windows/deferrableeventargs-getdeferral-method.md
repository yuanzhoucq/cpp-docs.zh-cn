---
title: "Deferrableeventargs:: Getdeferral 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d43aa6d82f44965e8defda2af3e6455e86cba38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral 方法
获取对[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)对象该对象表示延迟的事件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>参数  
 `result`  
 一个指针，它将引用[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)对象时在调用完成。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 有关代码示例，请参阅[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)