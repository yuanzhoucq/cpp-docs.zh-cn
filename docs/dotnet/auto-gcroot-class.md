---
title: auto_gcroot 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b6afad3450aff2a9243b3e4a480a374fbcd14fc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="autogcroot-class"></a>auto_gcroot 类
自动资源管理 (如[auto_ptr 类](../standard-library/auto-ptr-class.md)) 可用于本机类型中嵌入虚拟句柄。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>参数  
 `_element_type`  
 要嵌入的托管的类型。  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [auto_gcroot](../dotnet/auto-gcroot.md)   
 [auto_gcroot 成员](../dotnet/auto-gcroot-members.md)   
 [如何： 声明在本机类型中的句柄](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle 类](../dotnet/auto-handle-class.md)