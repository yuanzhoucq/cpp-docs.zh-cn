---
title: "支持在提供程序中自由线程处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d062a17fd71d53451aa8de3aa7d498f8a5ec68a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-free-threading-in-your-provider"></a>在提供程序中支持自由线程处理
所有 OLE DB 提供程序类都是线程安全的并相应地设置注册表项。 它是性能的一个好办法支持自由线程处理有助于提供高级别的在多用户情况下。 为了帮助保持你的提供商线程安全，必须验证你的代码被正确模块。 无论何时编写或存储数据，你必须阻止与临界区的访问权限。  
  
 每个 OLE DB 提供程序模板对象都有其自己的关键部分。 若要使模块化更容易，您创建的每个新类应该是一种模板类将父类名称作为自变量。  
  
 下面的示例演示如何阻止你的代码：  
  
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
  
 有关如何保护与临界区的详细信息`Lock`和`Unlock`，请参阅[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
 你还必须验证你替代任何方法 (如`Execute`) 都是线程安全。  
  
## <a name="see-also"></a>另请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)