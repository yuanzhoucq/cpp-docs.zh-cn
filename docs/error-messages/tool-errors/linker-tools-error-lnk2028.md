---
title: "链接器工具错误 LNK2028 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7441dcd893e3e814d738f228d002a947e7f43c8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2028"></a>链接器工具错误 LNK2028
"exported_function"(decorated_name) 函数"function_containing_function_call"(decorated_name) 中引用  
  
 当尝试将本机函数导入纯映像，请记住，本机和纯各编译间不同隐式调用约定。  
  
## <a name="example"></a>示例  
 此代码示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例创建一个使用本机函数的纯客户端。 但是，在下的调用约定**/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2028。  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```