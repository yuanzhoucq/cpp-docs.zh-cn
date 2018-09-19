---
title: auto_handle 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle, msclr::auto_handle
- msclr.auto_handle
dev_langs:
- C++
helpviewer_keywords:
- auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0bddacec4e416173fc60ceb1c2c6ee71b3a198e7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029710"
---
# <a name="autohandle-class"></a>auto_handle 类
自动资源管理，这可用于托管类型中嵌入虚拟句柄。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename _element_type>  
ref class auto_handle;  
```  
  
#### <a name="parameters"></a>参数  
*_element_type*<br/>
要嵌入的托管的类型。  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [auto_handle](../dotnet/auto-handle.md)   
 [auto_handle 成员](../dotnet/auto-handle-members.md)   
 [auto_gcroot 类](../dotnet/auto-gcroot-class.md)