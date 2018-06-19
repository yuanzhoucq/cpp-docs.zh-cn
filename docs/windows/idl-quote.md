---
title: idl_quote |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8844a4770d0a4746c9d9de32a593d0770dcc9a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878507"
---
# <a name="idlquote"></a>idl_quote
允许你使用 Visual c + + 的当前版本中不支持的 IDL 构造并将它们传递到生成的.idl 文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *文本*  
 你想 Visual c + + 编译器，而无需返回编译器错误传递给生成的.idl 文件中的特性名称。  
  
## <a name="remarks"></a>备注  
 如果**idl_quote**然后的独立特性 （与右括号后面的分号），使用 c + + 属性*文本*放置在合并的.idl 文件原样。 如果**idl_quote**使用上一个符号，*文本*放置在该符号的属性块内。  
  
## <a name="example"></a>示例  
 下面的代码演示如何可以指定不支持的属性 (使用**中**，这受支持) 以及如何定义和使用未定义的.idl 构造：  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 此代码会导致 MYFLOT 和 MYDUB 和*文本*条目以放置在生成的.idl 文件。 *名称*参数强制*文本*放置在引用的任何内容之前*名称*生成的.idl 文件中。 *依赖关系*参数强制前后放置的依赖项列表定义*文本*生成的.idl 文件中。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
