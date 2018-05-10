---
title: 'Deferrableeventargs:: Getdeferral 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2442894c5f7bd85eb94262e776294c1e52a19e01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral 方法
获取对[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)对象该对象表示延迟的事件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>参数  
 `result`  
 一个指针，它将引用[延迟](http://go.microsoft.com/fwlink/p/?linkid=526520)对象时在调用完成。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 有关代码示例，请参阅[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)