---
title: 'Safeintexception:: Safeintexception |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 744bf034572745cd88a35f47a1ca2da03e900fd8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606652"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
创建**SafeIntException**对象。  
  
## <a name="syntax"></a>语法  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>参数  
 [in]*代码*  
 一个枚举的数据值，描述发生的错误。  
  
## <a name="remarks"></a>备注  
 可能的值*代码*文件 Safeint.h 中定义。 为方便起见，还此处列出可能的值。  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** msl:: utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)   
 [SafeInt 类](../windows/safeint-class.md)