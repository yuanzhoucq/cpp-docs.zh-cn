---
title: "链接器工具错误 LNK1256 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 5e29e6100b57531c7a29f84e7c0feac53f20cec9
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="linker-tools-error-lnk1256"></a>链接器工具错误 LNK1256
ALINK 操作失败︰ 原因  
  
 LNK1256 的一个常见原因是程序集的版本号出错。 程序集版本号的任何部分均不允许值 65535。 程序集版本的有效范围是 0-65534。  
  
 如果 ALINK 找不到已命名的密钥容器，也可能导致 LNK1256。 删除密钥容器，然后通过使用到的强名称 CSP 再次添加它[Sn.exe （强名称工具）](http://msdn.microsoft.com/Library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)。  
  
 LNK1256 的另一个原因是链接器和 Alink.dll 之间的版本不匹配。 原因可能是安装了损坏的 Visual Studio。 使用**程序和功能**Windows 控制面板来修复或重新安装 Visual Studio 中。  
  
 以下示例生成 LNK1256：  
  
```  
// LNK1256.cpp  
// compile with: /clr /LD  
// LNK1256 expected  
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];  
public class CMyClass {  
public:  
   int value;  
};  
```
