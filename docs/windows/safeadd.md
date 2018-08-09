---
title: SafeAdd |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ff51780cc05a4c133975d95dc89455a90e717d1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014599"
---
# <a name="safeadd"></a>SafeAdd
防止溢出的方式添加两个数字。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>参数  
 [in]*t*  
 要添加的第一个数。 其类型必须为 T。  
  
 [in]*u*  
 要添加的第二个数字。 其类型必须为 U。  
  
 [out]*结果*  
 参数位置**SafeAdd**将结果存储。  
  
## <a name="return-value"></a>返回值  
 **true**如果未发生错误;**false**如果发生错误。  
  
## <a name="remarks"></a>备注  
 此方法属于[SafeInt 库](../windows/safeint-library.md)，而无需创建的实例的适用的单个加法运算[SafeInt 类](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法仅应在必须保护单个数学运算时使用。 如果存在多个运算，则应使用 `SafeInt` 类而不是调用各个独立函数。  
  
 有关模板类型 T 和 U 的详细信息，请参阅[SafeInt 函数](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** microsoft:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeSubtract](../windows/safesubtract.md)