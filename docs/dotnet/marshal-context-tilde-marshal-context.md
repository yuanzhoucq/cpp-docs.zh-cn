---
title: 'marshal_context:: ~ marshal_context |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6cb7ed3c7b1ee5b28c4943d83b6a8ca6166b6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138083"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context
销毁 `marshal_context` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>备注  
 某些数据转换需要封送上下文。 请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)有关哪些翻译需要上下文，并且的封送处理文件具有要包括在你的应用程序的详细信息。  
  
 删除 `marshal_context` 对象将使由此上下文转换的数据失效。 如果要在销毁 `marshal_context` 对象之后保留数据，则必须手动将数据复制到将保持的变量中。  
  
## <a name="requirements"></a>要求  
 **标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>请参阅  
 [C + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 类](../dotnet/marshal-context-class.md)