---
title: 'Weakref:: Copyto 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d83ff273d3f6e9748be722b47d08c459564aa911
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo 方法
如果可用，请为指定的指针变量分配一个指向接口的指针。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 指向 IInspectable 接口的指针。 如果 `U` 不是派生自 IInspectable，则出现错误。  
  
 `riid`  
 接口 ID。 如果 `riid` 不是派生自 **IWeakReference**，则出现错误。  
  
 `ptr`  
 指向 IInspectable 或 IWeakReference 的双向间接指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为描述失败的 HRESULT。 有关更多信息，请参见“备注”。  
  
## <a name="remarks"></a>备注  
 返回值 S_OK 表示此操作成功，但并不指示弱引用是否解析为强引用。 如果返回 S_OK，则测试参数 `p` 是否为强引用；即，参数 `p` 不等于 `nullptr`。  
  
 从 Windows 10 SDK 开始，如果无法获得弱引用，此方法不再将 WeakRef 实例设置为 `nullptr` ，因此应避免使用检查 `nullptr`的 WeakRef 的错误检查代码。 相反，应检查`ptr`为`nullptr`。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [WeakRef 类](../windows/weakref-class.md)