---
title: 'Classfactory:: Lockserver 方法 |Microsoft Docs'
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
ms.openlocfilehash: ee858346fdb70e136edfbc562c2dfffb1f63e462
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652365"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
增加或减少基础对象数量跟踪的当前**ClassFactory**对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
### <a name="parameters"></a>参数  
 *纷纷采用*  
 **true**要递增跟踪对象的数量。 **false**要递减跟踪对象的数量。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为 E_FAIL。  
  
## <a name="remarks"></a>备注  
 **ClassFactory**跟踪的基础实例中的对象[模块](../windows/module-class.md)类。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ClassFactory 类](../windows/classfactory-class.md)