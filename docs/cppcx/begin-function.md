---
title: "begin 函数 |Microsoft 文档"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::begin
dev_langs: C++
helpviewer_keywords: begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d47244e6428979f5319c9ee02f252ef3e559f7ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="begin-function"></a>begin 函数
返回指向指定接口参数所访问的集合开头的迭代器。  
  
## <a name="syntax"></a>语法  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模板类型参数。  
  
 `v`  
 向量的集合\<T > 或 VectorView\<T > 对象访问的 IVector\<T > 或 IVectorView\<T > 接口。  
  
 `i`  
 由 IIterable 访问的任意 Windows 运行时对象的集合\<T > 接口。  
  
### <a name="return-value"></a>返回值  
 指向集合开头的迭代器。  
  
### <a name="remarks"></a>备注  
 前两个模板函数返回迭代器，第三个模板函数返回输入迭代器。  
  
 返回的对象开始的 VectorIterator 是存储的类型 VectorProxy 元素的代理迭代器\<T >。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="requirements"></a>惠?  
 **标头：** collection.h  
  
 **命名空间：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)