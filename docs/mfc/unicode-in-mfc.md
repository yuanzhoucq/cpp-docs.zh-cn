---
title: "MFC 中的 Unicode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- wide characters, Unicode
- Unicode [MFC], MFC
- wide characters, encoding
- strings [MFC], Unicode
- Unicode [MFC], enabling
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc7ac9a55818022a4238565ed4309fe96f7ec058
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-in-mfc"></a>MFC 中的 Unicode
MFC 在 Windows NT、Windows 2000 和 Windows XP 平台上支持使用 Unicode 标准编码宽字符。 Unicode 应用程序无法在 Windows 98 平台上运行。  
  
 下面介绍了 MFC 库的 Unicode 版本：  
  
### <a name="static-link-libraries"></a>静态链接库  
  
|发布|调试|描述|  
|-------------|-----------|-----------------|  
|UAFXCW.lib、.pdb|UAFXCWD.lib、.pdb|Unicode MFC 静态链接库|  
  
### <a name="dynamic-link-libraries"></a>动态链接库  
  
|发布|调试|描述|  
|-------------|-----------|-----------------|  
|MFC100U.lib、.dbg、def、.dll、.map、.pdb、.prf|MFC100UD.lib、.def、.dll、.map、.pdb|Unicode MFC 导入库（有关文件扩展名的说明，请参阅下面的注意）|  
|MFCS100U.lib、.pdb|MFCS100UD.lib、.pdb|包含必须静态链接到应用程序或 DLL 的代码的 Unicode MFC 导入库|  
  
 **文件类型**  
  
-   导入库文件具有扩展名 (.lib)。  
  
-   动态链接库文件具有扩展名 (.dll)。  
  
-   模块定义 (.def) 文件是包含定义 .exe 或 .dll 的语句的文本文件。  
  
-   映射 (.map) 文件是包含链接器在链接程序时使用的信息的文本文件。  
  
-   库 (.lib) 文件将与 MFC 的 DLL 版本一起使用。 这些文件包含必须静态链接到应用程序或 DLL 的代码。  
  
-   程序数据库 (.pdb) 文件包含调试和项目状态信息。  
  
-   调试 (.dbg) 文件包含 Visual C++ 调试器使用的信息（COFF FPO 和 CodeView）。  
  
 有关命名约定的详细信息，请参阅[库命名约定](../mfc/library-naming-conventions.md)。  
  
 有关 MFC 使用 Unicode 的信息，请参阅[字符串： Unicode 和多字节字符集 (MBCS) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
## <a name="see-also"></a>另请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)

