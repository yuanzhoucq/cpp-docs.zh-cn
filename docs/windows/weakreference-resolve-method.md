---
title: "Weakreference:: Resolve 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs: C++
helpviewer_keywords: Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4da4689ffd8fa0a633b3f481b0292d060e57345
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 接口 ID。  
  
 `ppvObject`  
 此操作完成后，一份当前的强引用如果强引用计数不为零。  
  
## <a name="return-value"></a>返回值  
  
-   如果此操作成功，强引用计数为零，则为 S_OK。 `ppvObject` 参数设置为 `nullptr`。  
  
-   如果此操作成功，强引用计数不为零，则为 S_OK。 `ppvObject`参数设置为强引用。  
  
-   否则为指示的原因的 HRESULT 此操作失败。  
  
## <a name="remarks"></a>备注  
 如果强引用计数不为零，请将指定的指针设置为当前的强引用值。  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [WeakReference Class1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)