---
title: "如何：将 SharePoint 站点配置为专用库 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sharepoint, 专用库"
  - "专用库, Sharepoint"
ms.assetid: 6c6ed45f-7e46-4ed0-8b5c-839dbbe3769f
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 如何：将 SharePoint 站点配置为专用库
可以创建描述并提供扩展作为专用库的 SharePoint 列表页，然后将该列表添加到“扩展和更新”。 有关更多信息，请参见[私有库](../Topic/Private%20Galleries.md)。  
  
 使用 SharePoint 创建专用库，  
  
1.  首先，为专用库创建列表页。  
  
2.  随后上载扩展 \(.vsix\) 文件作为列表页上的各项。  
  
> [!IMPORTANT]
>  出于安全原因，SharePoint 会阻止上载 .vsix 文件。 设置专用库时，请确保不会阻止 .vsix 文件。 有关详细信息，请参阅[管理阻止的文件类型](http://go.microsoft.com/fwlink/?LinkID=201253)。  
  
## 为专用库创建列表页  
 根据你部署到的 SharePoint 服务器的配置，以下步骤可能会有所不同。 一般而言，这些部署说明对于 SharePoint 的任何 WSP 扩展都是相同的。 有关可以用于管理 SharePoint 解决方案部署的 STSAdm 工具的说明，请参阅 MSDN 杂志网站上的[使用 SharePoint 2007 部署解决方案](http://go.microsoft.com/fwlink/?LinkId=220676)。  
  
#### 为专用库创建列表页  
  
1.  将 Visual Studio 扩展列表 \(.wsp\) 文件上载到 SharePoint 服务器。  
  
2.  在命令提示符处，执行以下命令以在 SharePoint 服务器上安装 .wsp 文件。  
  
     **stsadm –o addsolution –name VisualStudioExtensionsList.wsp**  
  
     **stsadm –o deploysolution –name VisualStudioExtensionsList.wsp –url http:\/\/\<SERVERNAME\> –allowCasPolicies –allowgacdeployment –immediate**  
  
     可能还必须通过 SharePoint 用户界面为子站点激活该功能，如下所示。  
  
    1.  在菜单栏上依次选择“网站操作”、“网站设置”、“管理网站功能”。  
  
    2.  选择“Visual Studio 扩展库”旁的“激活”按钮。  
  
    3.  将 Visual Studio 扩展库添加到所需子站点。  
  
 如果必须删除列表页，请使用以下步骤。  
  
#### 为专用库删除列表页  
  
1.  在命令提示符处，执行以下命令以在 SharePoint 服务器上删除 .wsp 文件。  
  
     **stsadm –o retractsolution –name VisualStudioExtensionsList.wsp –immediate**  
  
     **stsadm –o deletesolution –name VisualStudioExtensionsList.wsp**  
  
2.  在 SharePoint 中，收回并删除解决方案。  
  
## FAQ  
  
### 上载扩展时会发生什么情况？  
 上载 Visual Studio 扩展 \(.vsix\) 文件时，会从该文件中提取信息。 首先，嵌入的 .vsixmanifest 文件中的某些值（例如 VsixId、VsixVersion 等）会进行提取并存储为对应 SPListItem 上的隐藏元数据值。 其次，扩展的图标和 PreviewImage 文件会进行提取并存储在单独列表中。  
  
 图像存储在名为 *ListTitle*\_VSIXIcons 和 *ListTitle*\_VSIXPreviewImages 的图片库，其中 *ListTitle* 是存储 .vsix 文件的列表实例的名称。 为每个图像文件的名称提供对应 VSIX ID 作为前缀。  
  
### 删除扩展时会发生什么情况？  
 删除 .vsix 文件时，也会删除对应的图像文件（如果有）。  
  
### 更新扩展时会发生什么情况？  
 可以通过上载 .vsix 文件的新版本并覆盖现有版本来更新扩展。 更新扩展时，会根据新版本中的值更新扩展的所有元数据值和映像。  
  
### 删除列表时会发生什么情况？  
 删除 Visual Studio 扩展列表的实例时，也会删除对应 \_VSIXIcons 和 \_VSIXPreviewImages 图片库。  
  
### 支持哪些版本的 SharePoint？  
 当前仅支持 SharePoint 2010。  
  
## 请参阅  
 [私有库](../Topic/Private%20Galleries.md)