---
title: "/DLL（生成 DLL） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DLL 链接器选项 [C++]"
  - "-DLL 链接器选项"
  - "DLL 链接器选项 [C++]"
  - "DLL [C++], 生成"
  - "导出 DLL [C++], 指定导出"
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /DLL（生成 DLL）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DLL  
```  
  
## 备注  
 \/DLL 选项生成作为主输出文件的 DLL。  DLL 通常包含可由另一个程序使用的导出。  有三种指定导出的方法，按照建议的使用顺序依次为：  
  
1.  源代码中的 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md)  
  
2.  .def 文件中的 [EXPORTS](../../build/reference/exports.md) 语句  
  
3.  LINK 命令中的 [\/EXPORT](../../build/reference/export-exports-a-function.md) 规范  
  
 程序可使用一种以上的方法。  
  
 另一种生成 DLL 的方法是使用 **LIBRARY** 模块定义语句。  将 \/BASE 和 \/DLL 选项连用等效于 **LIBRARY** 语句。  
  
 不要在开发环境中指定该选项；该选项只在命令行上可用。  在用“应用程序向导”创建 DLL 项目时设置该选项。  
  
 请注意，如果您在预备步骤中创建了导入库，则在创建 .dll 之前，生成 .dll 时必须传递生成导入库时所传递的同一组对象文件。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“配置属性”文件夹。  
  
3.  单击“常规”属性页。  
  
4.  修改“配置类型”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)