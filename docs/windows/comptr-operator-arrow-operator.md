---
title: "Comptr:: Operator-&gt;运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator->
dev_langs: C++
helpviewer_keywords: operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28ac6f7dfc4e53e6aadc4fd082e10a0325124ee0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperator-gt-operator"></a>Comptr:: Operator-&gt;运算符
检索指向当前模板参数所指定类型的指针。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>返回值  
 指向由当前模板类型名称指定的类型的指针。  
  
## <a name="remarks"></a>备注  
 此帮助器函数中删除使用 STDMETHOD 宏导致不必要的开销。 此函数使 IUnknown 类型而不是虚拟专用。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)