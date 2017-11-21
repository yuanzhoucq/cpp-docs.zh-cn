---
title: "Comptr::&amp;运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator&
dev_langs: C++
helpviewer_keywords: operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b464a77fedf0d996210040b744faea0ee7372ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperatoramp-operator"></a>Comptr::&amp;运算符
释放与此关联的接口`ComPtr`对象，然后检索的地址`ComPtr`对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>返回值  
 对当前的弱引用`ComPtr`。  
  
## <a name="remarks"></a>备注  
 此方法不同于[comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) ，因为此方法释放的接口指针的引用。 使用`ComPtr::GetAddressOf`如果您要求的接口指针的地址，但不是想要发布该接口。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)