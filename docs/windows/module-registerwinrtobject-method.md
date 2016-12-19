---
title: "Module::RegisterWinRTObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterWinRTObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterWinRTObject 方法"
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::RegisterWinRTObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注册一个或多个 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象，以便其他应用程序可连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>参数  
 `serverName`  
 指定受此操作影响的对象子集的名称。  
  
 `activatableClassIds`  
 要注册的可激活 CLSID 的数组。  
  
 `cookie`  
 标识已注册类对象的值。 此值以后将用于撤销注册。  
  
 `count`  
 要注册的对象的数量。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)