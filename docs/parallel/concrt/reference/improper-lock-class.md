---
title: "improper_lock 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::improper_lock
dev_langs:
- C++
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 5a68573b8963fed90a4346fd421ef479c35dc247
ms.lasthandoff: 02/24/2017

---
# <a name="improperlock-class"></a>improper_lock 类
此类描述错误获取锁时引发的异常。  
  
## <a name="syntax"></a>语法  
  
```
class improper_lock : public std::exception;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[improper_lock 构造函数](#ctor)|已重载。 构造一个 `improper_lock exception`。|  
  
## <a name="remarks"></a>备注  
 通常情况下，在尝试获取非重入锁定以递归方式在同一环境时，将引发此异常。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `improper_lock`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-improperlock"></a><a name="ctor"></a>improper_lock 

 构造一个 `improper_lock exception`。  
  
```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 错误的描述性消息。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [critical_section 类](critical-section-class.md)   
 [reader_writer_lock 类](reader-writer-lock-class.md)

