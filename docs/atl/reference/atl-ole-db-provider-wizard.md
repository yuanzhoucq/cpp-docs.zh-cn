---
title: "ATL OLE DB 提供程序向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.provider.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 提供程序向导"
  - "ATL 项目, 添加 ATL OLE DB 提供程序"
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL OLE DB 提供程序向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此向导创建撰写 OLE DB 提供程序的类。  
  
## 备注  
 从 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 开始，此向导生成的注册脚本将在 **HKEY\_CURRENT\_USER**（而不是 **HKEY\_LOCAL\_MACHINE**）下注册其 COM 组件。  若要修改此行为，请设置 ATL 向导的**“为所有用户注册组件”**选项。  
  
 下表描述了 ATL OLE DB 提供程序向导的选项：  
  
 **简称**  
 键入将创建的提供程序的简称。  向导中的其他编辑框将基于您在此处键入的内容自动填充。  如果需要，您可以编辑其他名称框。  
  
 **Coclass**  
 coclass 的名称。  ProgID 名称将更改以与该名称匹配。  
  
 **特性化**  
 此选项指定向导是使用特性还是模板声明来创建提供程序类。  当选择此选项时，向导使用属性而不是模板声明（如果创建的是特性化项目，这是默认选项）。  当您清除此选项时，向导使用模板声明而不是属性（如果创建的是非特性化项目，这是默认选项）。  
  
 如果当创建的是非特性化项目时选择此选项，向导将警告您项目将转换为特性化项目，并询问您是否继续。  
  
 **ProgID**  
 ProgID（或程序标识符）是应用程序可以用来代替 GUID 的文本字符串。  ProgID 名称的形式为 *Projectname*.*Coclassname*。  
  
 **版本**  
 提供程序的版本号。  默认值为 1。  
  
 **数据源类**  
 数据源类的名称，其形式为 C`Shortname`Source。  
  
 **数据源 .h 文件**  
 数据源类的头文件。  可以编辑该文件的名称或选择现有的头文件。  
  
 **会话类**  
 会话类的名称，其形式为 C`Shortname`Session。  
  
 **会话 .h 文件**  
 会话类的头文件。  可以编辑该文件的名称或选择现有的头文件。  
  
 **Command 类**  
 命令类的名称，其形式为 C`Shortname`Command。  
  
 **命令 .h 文件**  
 命令类的头文件。  该名称无法编辑并且依赖于行集合头文件的名称。  
  
 **行集合类**  
 行集合类的名称，其形式为 C`Shortname`Rowset。  
  
 **行集 .h 文件**  
 行集合类的头文件。  可以编辑该文件的名称或选择现有的头文件。  
  
 **行集 .cpp 文件**  
 提供程序的实现文件。  可以编辑该文件的名称或选择现有的实现文件。  
  
## 请参阅  
 [ATL OLE DB Provider](../../atl/reference/adding-an-atl-ole-db-provider.md)