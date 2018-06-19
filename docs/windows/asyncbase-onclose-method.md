---
title: 'Asyncbase:: Onclose 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnClose
dev_langs:
- C++
helpviewer_keywords:
- OnClose method
ms.assetid: 96766450-c262-4611-8534-7d190b799142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95a0cce7f51ef7974d0520f0bdfd2f025a09ecaf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859600"
---
# <a name="asyncbaseonclose-method"></a>AsyncBase::OnClose 方法
当在派生类中重写，关闭异步操作。  
  
## <a name="syntax"></a>语法  
  
```  
virtual void OnClose(  
   void  
) = 0;  
```  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)   
 [AsyncBase::Close 方法](../windows/asyncbase-close-method.md)