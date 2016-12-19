---
title: "Semaphore::operator= 运算符 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 运算符"
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore::operator= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将指定的句柄从信号量对象移动到当前的信号量对象。  
  
## <a name="syntax"></a>语法  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 信号量对象对右值引用。  
  
## <a name="return-value"></a>返回值  
 对当前的信号量对象的引用。  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另请参阅
 [Semaphore 类](../windows/semaphore-class.md)