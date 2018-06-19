---
title: 'Safeintexception:: Safeintexception |Microsoft 文档'
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
ms.openlocfilehash: ef3c1d11c0f814699ca1492f7ec1fb49c43c3d76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892171"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
创建一个 `SafeIntException` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `code`  
 一个枚举的数据值，描述发生的错误。  
  
## <a name="remarks"></a>备注  
 可能值`code`文件 Safeint.h 中定义。 为方便起见，还此处列出了可能的值。  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>要求  
 **标头：** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)   
 [SafeInt 类](../windows/safeint-class.md)