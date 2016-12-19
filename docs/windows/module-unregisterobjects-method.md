---
title: "Module::UnregisterObjects 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::UnregisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterObjects 方法"
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::UnregisterObjects 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消指定模块中的对象，以便其他应用程序无法连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>参数  
 `module`  
 指向模块的指针。  
  
 `serverName`  
 指定受此操作影响的对象子集的限定名。  
  
## <a name="return-value"></a>返回值  
 如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)