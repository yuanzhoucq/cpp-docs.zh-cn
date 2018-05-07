---
title: 链接器工具错误 LNK1179 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1179"></a>链接器工具错误 LNK1179
无效或已损坏的文件： 重复 COMDAT filename  
  
 对象模块包含具有相同名称的两个或多个 Comdat。  
  
 使用可导致此错误[/H](../../build/reference/h-restrict-length-of-external-names.md)，这就限制了外部名称的长度和[/Gy](../../build/reference/gy-enable-function-level-linking.md)的包中的 Comdat 函数。  
  
## <a name="example"></a>示例  
 在下面的代码中，`function1`和`function2`相同的前八个字符。 使用编译 **/Gy**和 **/H8**产生链接错误。  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```