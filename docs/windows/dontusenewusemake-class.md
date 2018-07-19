---
title: DontUseNewUseMake 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f343d0b47d50cd375d186c29ff55b91898aa9c61
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872323"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>备注  
 阻止使用运算符`new`RuntimeClass 中。 因此，必须使用[使函数](../windows/make-function.md)相反。  
  
## <a name="members"></a>成员  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new 运算符](../windows/dontusenewusemake-operator-new-operator.md)|重载运算符`new`和阻止它在 RuntimeClass 中使用。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make 函数](../windows/make-function.md)