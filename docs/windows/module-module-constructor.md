---
title: "Module::Module 构造函数 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "模块, 构造函数"
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::Module 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Module 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
Module();  
```  
  
## <a name="remarks"></a>备注  
 此构造函数受保护，不能使用 `new` 关键字进行调用。 请调用 [module:: getmodule 方法](../windows/module-getmodule-method.md) 或 [module:: create 方法](../windows/module-create-method.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)