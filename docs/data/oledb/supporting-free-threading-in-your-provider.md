---
title: "在提供程序中支持自由线程处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 多线程"
  - "线程处理 [C++], 提供程序"
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在提供程序中支持自由线程处理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有 OLE DB 提供程序类都是线程安全的，并且相应地设置注册表项。  支持自由线程处理是一个好主意，因为这有助于在多用户情况下提供高级性能。  为使提供程序是线程安全的，必须确保代码被正确模块化。  每当写入或存储数据时，都必须用临界区将访问模块化。  
  
 每个 OLE DB 提供程序模板对象都有自己的临界区。  为使模块化更容易，创建的每个新类应该是将父类名用作参数的模板类。  
  
 下面的示例显示如何模块化代码：  
  
```  
template <class T>  
class CMyObject<T> : public...  
  
HRESULT MyObject::MyMethod(void)  
{  
   T* pT = (T*)this;      // this gets the parent class   
  
// You don't need to do anything if you are only reading information  
  
// If you want to write information, do the following:  
   pT->Lock();         // engages critical section in the object  
   ...;                // write whatever information you wish  
   pT->Unlock();       // disengages the critical section  
}  
```  
  
 有关如何用 `Lock` 和 `Unlock` 保护临界区的更多信息，请参见 [多线程编程：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
 还必须确保重写的任何方法（如 `Execute`）是线程安全的。  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)