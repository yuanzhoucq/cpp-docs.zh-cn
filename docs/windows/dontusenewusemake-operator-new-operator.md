---
title: 'Dontusenewusemake:: Operator new 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9785ea27c79ff0a118ff3697a22804c520b265ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new 运算符
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### <a name="parameters"></a>参数  
 `__unnamed0`  
 未命名的参数，指定要分配的内存的字节数。  
  
 `placement`  
 要分配的类型。  
  
## <a name="return-value"></a>返回值  
 使您能够将其他自变量传递如果重载运算符`new`。  
  
## <a name="remarks"></a>备注  
 重载运算符`new`和阻止它在 RuntimeClass 中使用。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [DontUseNewUseMake 类](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)