---
title: "ClassFactory::LockServer 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ClassFactory::LockServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LockServer 方法"
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory::LockServer 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

递增或递减当前 ClassFactory 对象跟踪的基础对象数量。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>参数  
 `fLock`  
若要递增跟踪对象的数量，则为  `true`。 若要递减跟踪对象的数量，则为 `false`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为 E_FAIL。  
  
## <a name="remarks"></a>备注  
 ClassFactory 将跟踪的对象的基础实例中 [模块](../windows/module-class.md) 类。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ClassFactory 类](../windows/classfactory-class.md)