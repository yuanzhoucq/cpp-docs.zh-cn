---
title: marshal_context::marshal_context |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e8838864c4ec1c6414401608b848cb12b01c16e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context
构造`marshal_context`用于托管和本机数据类型之间的数据转换对象。  
  
## <a name="syntax"></a>语法  
  
```  
marshal_context();  
```  
  
## <a name="remarks"></a>备注  
 某些数据转换需要封送上下文。 请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)有关哪些翻译需要上下文，并且的封送处理文件具有要包括在你的应用程序的详细信息。  
  
## <a name="example"></a>示例  
 请参阅示例[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。  
  
## <a name="requirements"></a>要求  
 **标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>请参阅  
 [C + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 类](../dotnet/marshal-context-class.md)