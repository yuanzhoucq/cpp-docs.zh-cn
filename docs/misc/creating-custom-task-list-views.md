---
title: "创建自定义任务列表视图 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "任务列表，自定义视图"
ms.assetid: c25f8f5d-55a1-4b5e-b617-3d1140bcb98a
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 创建自定义任务列表视图
在 Visual Studio 中显示自定义任务列表通过创建自定义任务列表视图。  
  
 使用注册表来创建自定义视图并进行这些规范:  
  
-   列  
  
-   列的排序顺序  
  
-   这是默认排序顺序  
  
-   要显示的任务类别  
  
 可以显示自定义类别或为多个类别指定 CAT\_ALL。  您还可以创建包含所有文本的自定义文本列。  但是，您在自定义文本列不能排序。  
  
 下表显示自定义注册表布局任务列表视图。  
  
 在每一个表中， *与根 Reg* 使用 HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio \\ 8.0 \\。相等  表为每个注册表语句提供了脚本项和其他信息。  
  
 \[*与根 Reg*\\TaskList\\Views \\*GUID*\]  
  
|名称|类型|范围|说明|  
|--------|--------|--------|--------|  
|名称|REG\_SZ|Text|视图或 \#xxx 的字符串名称。<br /><br /> 名称可以与 “我的自定义视图的”普通字符串或它可以位于包 \(\#xxx\) 中的资源字符串。|  
|Package|REG\_SZ|Text|\[选择\] GUID 的字符串表示形式。  必需的某些字符串是否为资源字符串 \(\#xxx\);否则，它将被忽略。|  
  
 \[*与根 Reg*\\TaskList\\Views \\*GUID*\\Columns \\*数字*\]  
  
> [!NOTE]
>  *数字* 是列的从 1 开始的顺序在视图中 \(其中 1 是最左边的列\)。  有关更多列，增量 *数字*。  
  
|名称|类型|范围|说明|  
|--------|--------|--------|--------|  
|字段|REG\_DWORD||是列的字段的 <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> 。|  
|宽度|REG\_DWORD||可选。  列的宽度（以像素为单位）。  如果列不是相当大的，此参数将被忽略。|  
|索引|REG\_DWORD||可选。  如果字段是 FLD\_CUSTOM，这是自定义列索引。|  
|名称|REG\_SZ|Text|如果字段是 FLD\_CUSTOM，这是自定义列的名称。<br /><br /> 名称也是一个资源字符串 \#xxx 格式。|  
|Filter|REG\_SZ 或 REG\_DWORD||任何具有内置 VSTASKCATEGORY 或一个字符串表示自定义类别 GUID 的 DWORD。|  
  
 \[*与根 Reg*\\TaskList\\Views \\*GUID*\\Sort \\*数字*\]  
  
> [!NOTE]
>  *数字* 标识排序关键字。  例如，对于主要排序关键字， *数字* 等于 1。  对于次要排序关键字， *数字* 等于 2，依此类推。  
  
|名称|类型|范围|说明|  
|--------|--------|--------|--------|  
|字段|REG\_DWORD||是列的字段的 <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> 。|  
|索引|REG\_DWORD||可选。  如果字段是 FLD\_CUSTOM，这是自定义列索引。|  
  
 若要实现自定义列，则必须实现在任务项的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2> 接口，并且必须实现该接口的以下方法:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.get_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.put_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.IsCustomColumnReadOnly%2A>  
  
 通过使用特定视图，的自定义列数当要求，任务列表查询 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2> 实现，由 *某些 GUID*。  如果任务包含有关该列的相应信息在该视图中，您提供信息该列，并指定该文本是否为只读。  
  
## 请参阅  
 [如何：创建任务列表的自定义类别](../misc/how-to-create-custom-categories-of-task-lists.md)