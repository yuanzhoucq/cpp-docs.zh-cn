---
title: "Mutex::operator= 运算符 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 运算符"
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mutex::operator= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

分配 （移动） 指定互斥体对象传递给当前 Mutex 对象。  
  
## <a name="syntax"></a>语法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>参数  
 `h`  
 Rvalue 引用对 Mutex 对象。  
  
## <a name="return-value"></a>返回值  
 对当前 Mutex 对象的引用。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅 **移动语义** 部分 [Rvalue 引用声明符︰ & （& a)](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另请参阅
 [Mutex 类](../windows/mutex-class1.md)