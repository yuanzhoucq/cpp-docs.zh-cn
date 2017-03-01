---
title: "链接器工具错误 LNK2005 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf93f364b3dc7156a62eb1c474177eb7b85c7827
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2005"></a>链接器工具错误 LNK2005
对象中已定义的符号  
  
以修饰形式显示的给定 `symbol` 被多次定义。  
  
有关详细信息，请参阅知识库文章：  
  
-   [在 Visual c + + 中的顺序不正确链接的 CRT 库和 MFC 库时发生 LNK2005 错误](https://support.microsoft.com/kb/148652)  
  
-   [FIX︰ 全局重载的删除运算符导致 LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [在编译 Visual c + + ATL 可执行文件 (.exe) 项目时收到 LNK2005 错误](https://support.microsoft.com/kb/184235)。  
  
此错误之后为致命错误[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  此外使用时混合静态和动态库[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
2.  该符号为封装的函数 (与编译时所创建[/Gy](../../build/reference/gy-enable-function-level-linking.md))，包含在多个文件，但各编译间已改变。 重新编译所有包含 `symbol` 的文件。  
  
3.  以不同的形式在不同库中的两个成员对象中定义了该符号，并且使用了这两个成员对象。  
  
4.  某个绝对符号被定义两次，而每次定义的值都不同。  
  
5.  头文件声明并定义了变量。 可能的解决方案包括：  
  
    -   在 .h 中声明变量：`extern BOOL MyBool;`，然后在 .c 或 .cpp 文件中向它分配：`BOOL MyBool = FALSE;`。  
  
    -   将变量声明为[静态](../../cpp/storage-classes-cpp.md#static)。  
  
    -   将变量声明为[selectany](../../cpp/selectany.md)。  
  
6.  当将 uuid.lib 与定义 GUID 的其他 .lib 文件（例如 oledb.lib 和 adsiid.lib）一起使用时。 例如:   
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要修复，请添加[/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md)到链接器命令行选项，并确保 uuid.lib 是引用的第一个库。
