---
title: "链接器工具错误 LNK1256 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs: C++
helpviewer_keywords: LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbbb14e4f4fdef63b58bdef5ecafcfe0b045f412
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1256"></a>链接器工具错误 LNK1256
ALINK 操作失败： 原因  
  
 LNK1256 的一个常见原因是程序集的版本号出错。 程序集版本号的任何部分均不允许值 65535。 程序集版本的有效范围是 0-65534。  
  
 如果 ALINK 找不到已命名的密钥容器，也可能导致 LNK1256。 删除密钥容器，然后通过使用到的强名称 CSP 再次添加它[Sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)。  
  
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