---
title: 锁定类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a860f79b740e0f34eef33b7a96e0236835f1f6b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129692"
---
# <a name="lock-class"></a>lock 类
此类自动执行采用以从多个线程同步到对象的访问的锁定。  在构造时它获取该锁和销毁它版本时锁定。  
  
## <a name="syntax"></a>语法  
  
```  
ref class lock;  
```  
  
## <a name="remarks"></a>备注  
 `lock` 仅适用于 CLR 对象和仅可在 CLR 代码。  
  
 在内部，锁类使用<xref:System.Threading.Monitor>的访问进行同步。 在同步，请参阅本主题更多详细信息。  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [lock](../dotnet/lock.md)   
 [lock 成员](../dotnet/lock-members.md)