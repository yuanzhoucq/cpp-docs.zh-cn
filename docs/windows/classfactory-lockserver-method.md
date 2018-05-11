---
title: 'Classfactory:: Lockserver 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e09a795688c7e2b31771126f9e4036ddfbd8e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
递增或递减当前 ClassFactory 对象跟踪的基础对象数量。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>参数  
 `fLock`  
 若要递增跟踪对象的数量，则为 `true`。 若要递减跟踪对象的数量，则为 `false`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为 E_FAIL。  
  
## <a name="remarks"></a>备注  
 ClassFactory 将跟踪的基础实例中的对象[模块](../windows/module-class.md)类。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ClassFactory 类](../windows/classfactory-class.md)