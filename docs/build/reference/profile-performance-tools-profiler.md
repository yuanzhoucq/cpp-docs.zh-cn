---
title: /PROFILE（性能工具分析器）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 23cbccba9a8ec839252d553cc5cbafd37e66bbf9
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124767"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE（性能工具分析器）

生成一个可与“性能工具”探查器结合使用的输出文件。

## <a name="syntax"></a>语法

```
/PROFILE
```

## <a name="remarks"></a>备注

/ 配置文件表示以下链接器选项：

- [/OPT:REF](opt-optimizations.md)

- /OPT:NOICF

- [/INCREMENTAL:NO](incremental-link-incrementally.md)

- [/FIXED:NO](fixed-fixed-base-address.md)

/ 配置文件会导致链接器在程序映像中生成重定位节。  重定位节允许探查器来转换在程序映像，以获取配置文件数据。

**/ 分析**只是仅在 Enterprise （团队开发） 版本中可用。  PREfast 的详细信息，请参阅[于 c 语言的代码分析 /C++概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**配置文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>若要设置 Visual Studio 的 CMake 项目中此链接器选项

**CMake**的项目不具有**属性页**，链接器选项都可以设置有所通过 CMakeLists.txt。

1. 在项目根目录中打开 CMakeLists.txt。

1. 添加下面的代码。 有关详细信息，请参阅[CMake 的引用](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. 重新生成解决方案。

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)

