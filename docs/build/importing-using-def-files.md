---
title: "使用 DEF 文件导入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def 文件 [C++], 导入"
  - "def 文件 [C++], 导入"
  - "dllimport 特性 [C++], DEF 文件"
  - "DLL [C++], DEF 文件"
  - "导入 DLL [C++], DEF 文件"
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 DEF 文件导入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果选择与 .def 文件一起使用 **\_\_declspec\(dllimport\)**，则应更改 .def 文件，用 DATA 取代 CONSTANT，以减少因不正确的编码导致问题的可能性：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 下表说明了原因。  
  
|关键字|在导入库中发出|导出|  
|---------|-------------|--------|  
|`CONSTANT`|`_imp_ulDataInDll_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 使用 **\_\_declspec\(dllimport\)** 和 CONSTANT，在为允许显式链接而创建的 .lib DLL 导入库中同时列出 `imp` 版本和未修饰名。  使用 **\_\_declspec\(dllimport\)** 和 DATA 列出的只是 `imp` 版本的名称。  
  
 如果使用 CONSTANT，则可以使用以下任一代码构造访问 `ulDataInDll`：  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 \- 或 \-  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 但是，如果在 .def 文件中使用 DATA，则只有用下面的定义编译的代码才可以访问 `ulDataInDll` 变量：  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 使用 CONSTANT 的风险更大，因为如果忘记使用额外级别的间接寻址，则访问的有可能是指向变量的导入地址表的指针，而不是变量本身。  由于导入地址表当前被编译器和链接器设置成了只读，因此这类问题经常表现为访问冲突。  
  
 如果当前的 Visual C\+\+ 链接器发现 .def 文件中的 CONSTANT 是导致上述问题的原因，它将发出警告。  使用 CONSTANT 的唯一真正原因是：无法对头文件未在原型上列出 **\_\_declspec\(dllimport\)** 的某对象文件进行重新编译。  
  
## 请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)