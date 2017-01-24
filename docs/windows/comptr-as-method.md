---
title: "ComPtr::As 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::As"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "As 方法"
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::As 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回表示由指定模板参数标识的接口的 ComPtr 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 要由参数表示的接口 `p`。  
  
 `p`  
 一个表示参数所指定的接口的 ComPtr 对象 `U`。 参数 `p` 不得引用当前的 ComPtr 对象。  
  
## <a name="remarks"></a>备注  
 第一个模板是应在代码中使用的表单。 第二个模板是支持 c + + 语言功能，如的内部帮助器专用 [自动](../cpp/auto-cpp.md) 类型推导关键字。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)