---
title: "BoolStruct 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::BoolStruct
dev_langs: C++
helpviewer_keywords: BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7daa7527c8eea2cfca3b8933b9c3e1f042883e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="boolstruct-structure"></a>BoolStruct 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>备注  
 BoolStruct 结构定义是否 comptr 是否托管接口的对象生存期。 内部使用 BoolStruct [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)运算符。  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[BoolStruct::Member 数据成员](../windows/boolstruct-member-data-member.md)|指定[ComPtr](../windows/comptr-class.md) ，或不是，管理接口的对象生存期。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `BoolStruct`  
  
## <a name="requirements"></a>惠?  
 **标头：** internal.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType 运算符](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)