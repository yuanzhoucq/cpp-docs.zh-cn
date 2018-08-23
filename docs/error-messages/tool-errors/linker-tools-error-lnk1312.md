---
title: 链接器工具错误 LNK1312 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748276ed8fa459c41174f23d32bcef127cbdd510
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300441"
---
# <a name="linker-tools-error-lnk1312"></a>链接器工具错误 LNK1312
无效或已损坏的文件： 无法导入程序集  
  
 生成程序集、 模块或使用编译的程序集之外的文件时 **/clr**传递到**进行**链接器选项。  如果传递的对象文件**进行**，只是该对象直接传递到链接器，而不是到**进行**。  
  
## <a name="example"></a>示例  
 下面的示例创建的.obj 文件。  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1312。  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```