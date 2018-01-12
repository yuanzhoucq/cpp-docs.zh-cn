---
title: "back_inserter 函数 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::back_inserter
dev_langs: C++
helpviewer_keywords: back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 175842a495bda037aca1b59ed7de12c0635b67f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="backinserter-function"></a>back_inserter 函数
返回用于在指定集合末尾插入元素的迭代器。  
  
## <a name="syntax"></a>语法  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型参数。  
  
 `v`  
 提供对基础集合访问的接口指针。  
  
### <a name="return-value"></a>返回值  
 迭代器。  
  
### <a name="requirements"></a>惠?  
 **标头：** collection.h  
  
 **命名空间：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)