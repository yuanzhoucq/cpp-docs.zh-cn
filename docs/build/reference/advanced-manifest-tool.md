---
title: 属性高级清单工具配置&lt;项目名称 > 属性页对话框
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
ms.assetid: 3d587366-05ea-4956-a978-313069660735
ms.openlocfilehash: a20e474deb69099c53ad656dda5406e7161a1695
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295131"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>“&lt;项目名&gt;属性页”对话框 ->“配置属性”->“清单工具”->“高级”

使用此对话框指定 [Mt.exe](https://msdn.microsoft.com/library/aa375649) 的高级选项。

若要访问此属性页对话框，请打开项目或属性表的属性页。 展开“配置属性”下的“清单工具节点”，然后选择“高级”。

## <a name="uielement-list"></a>UIElement 列表

- **更新文件哈希**

   使用 /hashupdate 选项，指定该清单工具将计算在 `<file>` 元素中指定的文件哈希，然后使用计算的值更新哈希特性。

- **更新文件哈希搜索路径**

   指定在 `<file>` 元素中引用的文件的搜索路径。 此选项也使用 /hashupdate 选项。

## <a name="see-also"></a>请参阅

[\<file> 元素](/visualstudio/deployment/file-element-clickonce-application)<br>
[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br>
[清单工具属性页](manifest-tool-property-pages.md)<br>
[在 Visual Studio 中设置 C++ 编译器并生成属性](../working-with-project-properties.md)
