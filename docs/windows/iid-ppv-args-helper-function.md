---
title: "IID_PPV_ARGS_Helper 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/IID_PPV_ARGS_Helper
dev_langs: C++
helpviewer_keywords: IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9839fe71439fde54545a18ef107cec178b8bdcd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 函数
验证指定的参数的类型派生自`IUnknown`接口。  
  
> [!IMPORTANT]
>  此模板专用化支持 WRL 基础结构，不宜在代码中直接使用。 使用[IID_PPV_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx)相反。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 自变量的类型`pp`。  
  
 `pp`  
 双向间接指针。  
  
## <a name="return-value"></a>返回值  
 自变量`pp`强制转换为指针-到-a-指向的指针`void`。  
  
## <a name="remarks"></a>备注  
 如果将生成编译时错误的模板参数`T`不派生自`IUnknown`。  
  
## <a name="requirements"></a>惠?  
 **标头：** client.h  
  
## <a name="see-also"></a>请参阅  
 [参考 （Windows 运行时库）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)