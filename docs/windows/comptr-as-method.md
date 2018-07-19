---
title: 'Comptr:: As 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb9fd0ff09f6775a95ff881d9f8cbaa3edc61065
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857267"
---
# <a name="comptras-method"></a>ComPtr::As 方法
返回表示由指定模板参数标识的接口的 ComPtr 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 要由参数表示的接口`p`。  
  
 `p`  
 表示由参数指定的接口的 ComPtr 对象`U`。 参数`p`不得引用当前 ComPtr 对象。  
  
## <a name="remarks"></a>备注  
 第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)