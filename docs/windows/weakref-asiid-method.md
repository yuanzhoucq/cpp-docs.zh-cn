---
title: "WeakRef::AsIID 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakRef::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置指定的 ComPtr 指针参数以表示指定的接口 ID。  
  
## 语法  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### 参数  
 `riid`  
 接口 ID。  
  
 `ptr`  
 此操作完成后，返回一个表示参数 `riid` 的对象。  
  
## 返回值  
  
-   如果此操作成功，则为 S\_OK；否则为指示此操作失败原因的错误 HRESULT，并且 `ptr` 被设置为 `nullptr`。  
  
-   如果此操作成功，但已释放当前 WeakRef 对象，则为 S\_OK。 参数 `ptr` 被设置为 `nullptr`。  
  
-   如果此操作成功，但当前 WeakRef 对象不是派生自参数 `riid`，则为 S\_OK。 参数 `ptr` 被设置为 `nullptr`。 \(有关更多信息，请参阅“备注”。\)  
  
## 备注  
 如果参数 `riid` 不是派生自 IInspectable，则出现错误。 此错误将取代返回值。  
  
 第一个模板是应在代码中使用的表单。 第二个模板（此处未显示，但在头文件中声明）是支持 [自动](../cpp/auto-cpp.md)类型推导关键字等 C\+\+ 语言功能的内部专用帮助器。  
  
 从 Windows 10 SDK 开始，如果无法获得弱引用，此方法不再将 WeakRef 实例设置为 `nullptr`，因此应避免使用检查 `nullptr` 的 WeakRef 的错误检查代码。 相反，应检查返回的 HRESULT 以确定方法是否成功，或检查 `nullptr` 的 `ptr`。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [WeakRef 类](../windows/weakref-class.md)