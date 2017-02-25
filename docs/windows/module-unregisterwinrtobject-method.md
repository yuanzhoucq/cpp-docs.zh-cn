---
title: "Module::UnregisterWinRTObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::UnregisterWinRTObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterWinRTObject 方法"
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Module::UnregisterWinRTObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注销一个或多个 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象，以便其他应用程序无法连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `cookie`  
 指针，其指向标识将撤销其注册的类对象的值。  
  
## <a name="return-value"></a>返回值  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)