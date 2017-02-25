---
title: "WeakRef::CopyTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo 方法"
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# WeakRef::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果可用，请为指定的指针变量分配一个指向接口的指针。  
  
## 语法  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<  
   typename U  
>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### 参数  
 `U`  
 指向 IInspectable 接口的指针。 如果 `U` 不是派生自 IInspectable，则出现错误。  
  
 `riid`  
 接口 ID。 如果 `riid` 不是派生自 **IWeakReference**，则出现错误。  
  
 `ptr`  
 指向 IInspectable 或 IWeakReference 的双向间接指针。  
  
## 返回值  
 如果成功，则为 S\_OK；否则为描述失败的 HRESULT。 有关更多信息，请参见“备注”。  
  
## 备注  
 返回值 S\_OK 表示此操作成功，但并不指示弱引用是否解析为强引用。 如果返回 S\_OK，则测试参数 `p` 是否为强引用；即，参数 `p` 不等于 `nullptr`。  
  
 从 Windows 10 SDK 开始，如果无法获得弱引用，此方法不再将 WeakRef 实例设置为 `nullptr`，因此应避免使用检查 `nullptr` 的 WeakRef 的错误检查代码。 相反，应检查返回的 HRESULT 以确定方法是否成功，或检查 `nullptr` 的 `ptr`。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [WeakRef 类](../windows/weakref-class.md)