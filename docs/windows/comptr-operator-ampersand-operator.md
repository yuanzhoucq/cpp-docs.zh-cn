---
title: 'Comptr:: Operator&amp;运算符 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0afff1699a4c7a3a14f07967cfb5ba5727ba0320
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461557"
---
# <a name="comptroperatoramp-operator"></a>Comptr:: Operator&amp;运算符
释放与此关联的接口**ComPtr**对象，然后检索的地址**ComPtr**对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>返回值  
 对当前的弱引用**ComPtr**。  
  
## <a name="remarks"></a>备注  
 此方法不同于[comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) ，此方法释放接口指针的引用。 使用`ComPtr::GetAddressOf`时需要的接口指针的地址但不是想要发布该接口。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)