---
title: 'Hstring:: Operator&lt;运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de7ffb304a8b2f1567ed5510c276c454903ec930
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608399"
---
# <a name="hstringoperatorlt-operator"></a>Hstring:: Operator&lt;运算符
指示第一个参数是否小于第二个参数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
```  
  
#### <a name="parameters"></a>参数  
 *lhs*  
 要比较的第一个参数。 *lhs*可以是对引用**HString**。  
  
 *rhs*  
 要比较的第二个参数。 *rhs*可以是对引用**HString**。  
  
## <a name="return-value"></a>返回值  
 **true**如果*lhs*参数是小于*rhs*参数; 否则为**false**。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)