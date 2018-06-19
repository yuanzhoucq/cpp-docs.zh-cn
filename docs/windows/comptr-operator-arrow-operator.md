---
title: 'Comptr:: Operator-&gt;运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3cb3571207f328ad044ffd3f2f9b83bcebc7677e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870180"
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
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)