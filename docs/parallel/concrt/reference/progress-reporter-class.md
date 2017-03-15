---
title: "progress_reporter 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppltasks/concurrency::progress_reporter
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 11
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
ms.openlocfilehash: c6b4dfee5b5f9df98a36fcdac116182ced4cbe30
ms.lasthandoff: 02/24/2017

---
# <a name="progressreporter-class"></a>progress_reporter 类
进度报告器类允许报告特定类型的进度通知。 每个 progress_reporter 对象都是绑定到特定异步动作或操作的。  
  
## <a name="syntax"></a>语法  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>参数  
 `_ProgressType`  
 通过进度报告器报告的每个进度通知的负载类型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[progress_reporter 构造函数](#ctor)||  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[报表方法](#report)|向进度报告器绑定到的异步动作或操作发送进度报告。|  
  
## <a name="remarks"></a>备注  
 此类型仅可用于 Windows 应用商店应用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `progress_reporter`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppltasks.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora-progressreporter"></a><a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="a-namereporta-report"></a><a name="report"></a>报表 

 向进度报告器绑定到的异步动作或操作发送进度报告。  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>参数  
 `val`  
 向报表通过进度通知负载。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

