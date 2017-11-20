---
title: "链接器工具错误 LNK2031 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2031
dev_langs: C++
helpviewer_keywords: LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8732b9deaf1da2e27b8f95aed63d09e9f4c41dec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2031"></a>链接器工具错误 LNK2031
无法生成有关"function_declaration"decorated_name; p/invoke元数据中缺少的调用约定  
  
 当尝试将本机函数导入纯映像，请记住，本机和纯各编译间不同隐式调用约定。 有关纯映像的详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 此代码示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例创建一个使用本机函数的纯客户端。 但是，在下的调用约定**/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2031。  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用纯映像中的本机函数。 请注意显式**__cdecl**调用约定说明符。  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```