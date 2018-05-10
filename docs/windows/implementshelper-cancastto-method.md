---
title: 'Implementshelper:: Cancastto 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 9ae6fa17-d0b1-4e31-9ae5-da6ae4026e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6de971f2de2421a2d7987dab30ba73fa2d225b15
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="implementshelpercancastto-method"></a>ImplementsHelper::CanCastTo 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
HRESULT CanCastTo(  
   _In_ const IID &iid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 引用接口 id。  
  
 `ppv`  
 如果此操作成功，通过指定指向接口的指针`riid`或`iid`。  
  
 `iid`  
 引用接口 id。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 获取一个指针指向指定的接口 id。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [ImplementsHelper 结构](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)