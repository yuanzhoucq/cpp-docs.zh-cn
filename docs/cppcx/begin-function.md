---
title: begin 函数 |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4954e98c1e6f1da30e321aad0c0e37cc5c1ab994
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606527"
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
 任意对象集合的 Windows 运行时访问的 IIterable\<T > 接口。  
  
### <a name="return-value"></a>返回值  
 指向集合开头的迭代器。  
  
### <a name="remarks"></a>备注  
 前两个模板函数返回迭代器，第三个模板函数返回输入迭代器。  
  
 返回的对象开始的 VectorIterator 是存储类型 VectorProxy 元素的代理迭代器\<T >。 不过，代理对象对于用户代码应该不可见。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。  
  
### <a name="requirements"></a>要求  
 **标头：** collection.h  
  
 **命名空间：** Windows::Foundation::Collections  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)