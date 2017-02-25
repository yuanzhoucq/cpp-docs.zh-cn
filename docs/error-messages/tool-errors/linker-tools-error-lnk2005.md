---
title: "链接器工具错误 LNK2005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2005"
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 链接器工具错误 LNK2005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对象中已定义的符号  
  
 以修饰形式显示的给定 `symbol` 被多次定义。  
  
 有关详细信息，请参阅知识库文章：  
  
-   “在 MFC 库之前链接 Link C 运行库时出现 LNK2005 错误”\(Q148652\)  
  
-   “全局重载的删除运算符导致 LNK2005”\(Q140440\)  
  
-   “定义 \_ATL\_MIN\_CRT 时出现针对新建和删除的 LNK2005 错误”\(Q184235\)。  
  
 知识库文章位于 MSDN Library CD\-ROM 或 [http:\/\/support.microsoft.com\/search](http://support.microsoft.com/search) 上。  
  
 该错误之后为致命错误 [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### 通过检查以下可能的原因进行修复  
  
1.  在也使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 时混合静态库和动态库。  
  
2.  该符号为封装函数（通过用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 编译创建），包含在多个文件中，但在各编译间已改变。  重新编译所有包含 `symbol` 的文件。  
  
3.  以不同的形式在不同库中的两个成员对象中定义了该符号，并且使用了这两个成员对象。  
  
4.  某个绝对符号被定义两次，而每次定义的值都不同。  
  
5.  头文件声明并定义了变量。  可能的解决方案包括：  
  
    -   在 .h 中声明变量：`extern BOOL MyBool;`，然后在 .c 或 .cpp 文件中向它分配：`BOOL MyBool = FALSE;`。  
  
    -   将变量声明为 [static](../../misc/static-cpp.md)。  
  
    -   将变量声明为 [selectany](../../cpp/selectany.md)。  
  
6.  当将 uuid.lib 与定义 GUID 的其他 .lib 文件（例如 oledb.lib 和 adsiid.lib）一起使用时。  例如：  
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要修复，请将 [\/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) 添加到链接器命令行选项，并确保 uuid.lib 是引用的第一个库。