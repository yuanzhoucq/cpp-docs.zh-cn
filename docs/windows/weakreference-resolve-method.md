---
title: 'Weakreference:: Resolve 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93df4ebf46b187cab63fbfaed2e273c55e7c0d84
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013244"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
### <a name="parameters"></a>参数  
 *riid*  
 接口 ID。  
  
 *ppvObject*  
 此操作完成后，当前的强引用，如果强引用计数不为零的副本。  
  
## <a name="return-value"></a>返回值  
  
-   如果此操作是成功的强引用计数为零，则为 S_OK。 *PpvObject*参数设置为**nullptr**。  
  
-   如果此操作成功，则为 S_OK 和强引用计数为非零值。 *PpvObject*参数设置为强引用。  
  
-   否则，一个 HRESULT，指示的原因，此操作失败。  
  
## <a name="remarks"></a>备注  
 将指定的指针设置为当前的强引用值，如果强引用计数不为零。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [WeakReference 类 1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)