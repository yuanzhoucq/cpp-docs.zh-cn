---
title: "Asyncbase:: Oncancel 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs: C++
helpviewer_keywords: OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e46f673329697ef503dafcc6a3b683fa2224525a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel 方法
当在派生类中重写时取消异步操作。  
  
## <a name="syntax"></a>语法  
  
```  
virtual void OnCancel(  
   void  
) = 0;  
```  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)   
 [AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)