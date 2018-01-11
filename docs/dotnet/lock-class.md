---
title: "锁定类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs: C++
helpviewer_keywords: lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2f2a8e371803d33a2c42508ec595681ada3bab8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="lock-class"></a>lock 类
此类自动执行采用以从多个线程同步到对象的访问的锁定。  在构造时它获取该锁和销毁它版本时锁定。  
  
## <a name="syntax"></a>语法  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>备注  
 `lock`仅适用于 CLR 对象和仅可在 CLR 代码。  
  
 在内部，锁类使用<xref:System.Threading.Monitor>的访问进行同步。 在同步，请参阅本主题更多详细信息。  
  
## <a name="requirements"></a>惠?  
 **标头文件** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [锁](../dotnet/lock.md)   
 [lock 成员](../dotnet/lock-members.md)