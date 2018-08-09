---
title: Weakref::&amp;运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125ffe998e7c3f225f72e3fb47df4ef3525c37f9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649043"
---
# <a name="weakrefoperatoramp-operator"></a>Weakref::&amp;运算符
返回`ComPtrRef`对象，表示当前**WeakRef**对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>返回值  
 一个`ComPtrRef`对象，表示当前**WeakRef**对象。  
  
## <a name="remarks"></a>备注  
 这是不是要在代码中使用的内部帮助器运算符。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [WeakRef 类](../windows/weakref-class.md)