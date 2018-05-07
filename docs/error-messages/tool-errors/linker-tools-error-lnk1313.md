---
title: 链接器工具错误 LNK1313 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1313
dev_langs:
- C++
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613c2069443e580fb581798d9e1cc6d5781d7c91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1313"></a>链接器工具错误 LNK1313
检测到 ijw/native 模块；不能与纯模块链接  
  
 Visual c + + 的当前版本不支持将本机或混合托管/本机.obj 文件与编译的.obj 文件链接 **/clr: pure**。  
  
## <a name="example"></a>示例  
  
```  
// LNK1313.cpp  
// compile with: /c /clr:pure  
// a pure module  
int main() {}  
```  
  
## <a name="example"></a>示例  
  
```  
// LNK1313_b.cpp  
// compile with: /c /clr  
// an IJW module  
void test(){}  
```  
  
## <a name="example"></a>示例  
 下面的示例将生成 LNK1313。  
  
```  
// LNK1313_c.cpp  
// compile with: /link LNK1313.obj LNK1313_b.obj  
// LNK1313 warning expected  
```