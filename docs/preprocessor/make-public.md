---
title: make_public | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 484462d5a705297f65e82f70fccc23a81eeb719e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="makepublic"></a>make_public
指示本机类型应具有公共程序集可访问性。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma make_public(type)  
```  
  
### <a name="parameters"></a>参数  
 `type` 是需要具有公共程序集可访问性的类型的名称。  
  
## <a name="remarks"></a>备注  
如果要引用的本机类型来自无法更改的 .h 文件，则 `make_public` 会很有用。 若要在带有公共程序集可见性的类型中使用公共函数签名中的本机类型，则本机类型还必须具有公共程序集可访问性，否则编译器将发出警告。  
  
`make_public` 必须在全局范围内指定，并且它仅在从声明它的位置到源代码文件的结尾有效。  
  
本机类型可以是隐式或显式专用;请参阅[类型可见性](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)有关详细信息。  
  
## <a name="example"></a>示例  
以下示例是包含两个本机结构的定义的 .h 文件的内容。  
  
```cpp  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  
  
## <a name="example"></a>示例  
以下代码示例使用头文件并说明除非您使用 `make_public` 将本机结构显式标记为公共，否则当您尝试在公共托管类型中的公共函数签名中使用本机结构时，编译器将生成警告。  
  
```cpp  
// make_public_pragma.cpp  
// compile with: /c /clr /W1  
#pragma warning (default : 4692)  
#include "make_public_pragma.h"  
#pragma make_public(Native_Struct_1)  
  
public ref struct A {  
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK  
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692  
};  
```  
  
## <a name="see-also"></a>请参阅  
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)