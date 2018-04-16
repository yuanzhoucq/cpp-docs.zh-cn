---
title: "marshal_context::marshal_as |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e56e225d136fb02445eeeb398937adc075f2dae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as
对特定数据对象执行封送处理，以在托管和本机数据类型之间转换它。  
  
## <a name="syntax"></a>语法  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `input`  
 你想要封送到的值`To_Type`变量。  
  
## <a name="return-value"></a>返回值  
 类型的变量的`To_Type`的转换的值，它是`input`。  
  
## <a name="remarks"></a>备注  
 此函数将对特定数据对象执行封送处理。 此函数只能用于由中的表的转换[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
 如果你尝试封送数据类型不受支持的一对`marshal_as`将生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在编译时。 阅读出现此错误的详细信息提供的消息。 `C4996`可为多个仅已弃用的函数生成的错误。 将生成此错误的两个条件将尝试封送不支持的数据类型对，并尝试对需要上下文的转换使用 `marshal_as`。  
  
 封送处理库包含多个标头文件。 任何转换要求只有一个文件，但如果你需要进行其他转换，则可以包括其他文件。 `Marshaling Overview in C++`中的表指示每次转换应包含的封送处理文件。  
  
## <a name="example"></a>示例  
 此示例将为从 `System::String` 到 `const char *` 变量类型的封送处理创建上下文。 转换数据在删除上下文的行之后是无效的。  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## <a name="requirements"></a>惠?  
 **标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>请参阅  
 [C + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 类](../dotnet/marshal-context-class.md)