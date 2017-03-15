---
title: "Module::RegisterObjects 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterObjects 方法"
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Module::RegisterObjects 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注册 COM 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象，以便其他应用程序可以连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>参数  
 `module`  
 COM 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象的数组。  
  
 `serverName`  
 创建对象的服务器的名称。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
## <a name="see-also"></a>另请参阅
[Module 类](../windows/module-class.md)