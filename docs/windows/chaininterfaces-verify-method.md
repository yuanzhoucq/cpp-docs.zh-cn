---
title: 'Chaininterfaces:: Verify 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c83479434a936f32fb0f7367d8cd02c6676c74e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860689"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify 方法
验证模板参数 `I0` 到 `I9` 定义的每个接口是否继承自 IUnknown 和/或 IInspectable，以及验证 `I0` 是否继承自 `I1` 到 `I9`。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>备注  
 如果验证操作失败，则 `static_assert` 将发出描述失败的错误消息。  
  
## <a name="remarks"></a>备注  
 模板参数 `I0` 和 `I1` 为必需，参数 `I2` 到 `I9` 为可选。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)