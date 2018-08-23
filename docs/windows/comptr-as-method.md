---
title: 'Comptr:: As 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffb84fd072f4ddd3dc76445c720debef5c364642
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590430"
---
# <a name="comptras-method"></a>ComPtr::As 方法

返回**ComPtr**对象，表示由指定的模板参数标识的接口。

## <a name="syntax"></a>语法

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>参数

*U*  
要由参数表示的接口*p*。

*p*  
一个**ComPtr**对象，表示指定参数的接口*U*。参数*p*必须是当前指**ComPtr**对象。

## <a name="remarks"></a>备注

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)