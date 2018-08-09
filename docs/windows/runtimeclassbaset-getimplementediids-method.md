---
title: 'Runtimeclassbaset:: Getimplementediids 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a5c63a3b2dbbac934162f74abb8e742cc4418a7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018986"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 类型*实现*参数。  
  
 *实现*  
 为参数指定的类型的指针*T*。  
  
 *iidCount*  
 接口 Id 来检索最大数目。  
  
 *iid*  
 如果此操作成功，完成的接口实现的类型的 Id 数组*T*。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为描述错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 检索接口实现由指定类型的 Id 的数组。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [RuntimeClassBaseT 结构](../windows/runtimeclassbaset-structure.md)