---
title: marshal_as |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a209b1ee657d6ae6773ee88c64225a7dc5b4f49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="marshalas"></a>marshal_as
此方法将本机和托管环境之间的数据转换。  
  
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
 此方法是将本机和托管类型之间的数据转换的简便的方法。 若要确定支持哪些数据类型，请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)。 某些数据转换需要上下文。 可以通过使用这些数据类型将转换[marshal_context 类](../dotnet/marshal-context-class.md)。  
  
 如果你尝试封送数据类型不受支持的一对`marshal_as`将生成错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在编译时。 阅读出现此错误的详细信息提供的消息。 `C4996`可为多个仅已弃用的函数生成的错误。 这样的一个例子尝试封送不支持的数据类型的对。  
  
 封送处理库包含多个标头文件。 任何转换要求只有一个文件，但如果你需要进行其他转换，则可以包括其他文件。 若要查看哪些转换是与哪些文件相关联，查看中的表中`Marshaling Overview`。 无论何种转换的你想要命名空间要求是始终有效。  
  
## <a name="example"></a>示例  
 此示例是从封送`const char*`到`System::String`变量类型。  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## <a name="requirements"></a>惠?  
 **标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>请参阅  
 [C + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context 类](../dotnet/marshal-context-class.md)