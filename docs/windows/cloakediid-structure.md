---
title: "CloakedIid 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::CloakedIid
dev_langs: C++
helpviewer_keywords: CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5a10752fecadaf3a7f044e3c563931ae3cdbe1b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cloakediid-structure"></a>CloakedIid 结构
指示无法访问 IID 列表中指定接口的 RuntimeClass、Implements 和 ChainInterfaces 模板。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename T  
>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 接口不可见 （掩蔽）。  
  
## <a name="remarks"></a>备注  
 下面是如何使用 CloakedIid 的一个示例： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)