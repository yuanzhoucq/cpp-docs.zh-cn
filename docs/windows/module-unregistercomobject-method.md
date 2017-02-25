---
title: "Module::UnregisterCOMObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::UnregisterCOMObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterCOMObject 方法"
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::UnregisterCOMObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注销一个或多个 COM 对象，以阻止其他应用程序连接到它们。  
  
## <a name="syntax"></a>语法  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>参数  
 `serverName`  
 （未使用）  
  
 `cookies`  
 指针的数组，其指向标识要注销的类对象的值。 该数组通过创建 [RegisterCOMObject](../windows/module-registercomobject-method.md) 方法。  
  
 `count`  
 要注销的类的数量。  
  
## <a name="return-value"></a>返回值  
 如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)