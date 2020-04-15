---
title: C/C++ 独立应用程序和并行程序集疑难解答
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 0dc8488acc90f1a38a4c0de0f052590ef4f398af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335436"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>C/C++ 独立应用程序和并行程序集疑难解答

如果找不到依赖库，则加载 C/C++ 应用程序可能会失败。 本文介绍 C/C++ 应用程序未能加载的一些常见原因，并提供了用于解决问题的建议步骤。

如果应用程序未能加载的原因是其清单指定了对某个并行程序集的依赖项，而该程序集未作为私有程序集安装在可执行文件所在的文件夹中，也未安装在 %WINDIR%\WinSxS\ 文件夹中的本机程序集缓存中，则可能会显示以下错误消息之一（具体取决于尝试运行应用的 Windows 的版本）。

- 应用程序正常初始化(0xc0000135)失败。

- 由于应用程序配置不正确，应用程序未能启动。 重新安装应用程序可能会纠正这个问题。

- 系统无法执行指定的程序。

如果应用程序没有清单，并且依赖于 Windows 在典型搜索位置找不到的 DLL，可能会显示类似于此消息的错误消息：

- 此应用程序未启动，因为找不到*所需的 DLL。* 重新安装应用程序可能会修复此问题。

如果应用程序部署在未安装 Visual Studio 的计算机上，并且它在出现类似于以上消息的错误消息的情况下崩溃，请检查以下内容：

1. 按照["了解可视化应用程序的依赖性"中](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)所述的步骤C++ 。 Dependency Walker 可以显示应用程序或 DLL 的大多数依赖项。 如果观察到某些 DLL 缺失，请在尝试运行应用程序的计算机上安装它们。

1. 操作系统加载程序会使用应用程序清单加载应用程序所依赖的程序集。 清单可以作为资源嵌入在二进制文件中，或作为单独文件安装在应用程序文件夹中。 要检查清单是否嵌入到二进制文件中，请在 Visual Studio 中打开二进制文件，并在其资源列表中查找RT_MANIFEST。 如果找不到嵌入的清单，请查看应用程序文件夹中的文件，该文件名为类似<binary_name>。\<扩展>.清单。

1. 如果应用程序依赖于并行程序集，但不存在清单，则必须确保链接器为项目生成清单。 选中项目项目 **"项目属性**"对话框中的 **"生成清单**"链接器选项。

1. 如果清单嵌入在二进制文件中，请确保 RT_MANIFEST 的 ID 对于此类型的二进制文件是正确的。 有关要使用的资源 ID 的详细信息，请参阅将并行[程序集用作资源 （Windows）](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource)。 如果清单位于单独文件中，请在 XML 编辑器或文本编辑器中打开它。 有关部署清单和规则的详细信息，请参阅[清单](/windows/win32/sbscs/manifests)。

   > [!NOTE]
   > 如果嵌入式清单和单独清单文件同时存在，则操作系统加载程序使用嵌入式清单，忽略单独文件。 但是，在 Windows XP 中，情况相反 — 使用单独清单文件，而忽略嵌入式清单。

1. 我们建议将清单嵌入在每个 DLL 中，因为在通过 `LoadLibrary` 调用加载 DLL 时会忽略外部清单。 有关详细信息，请参阅[程序集清单](/windows/win32/SbsCs/assembly-manifests)。

1. 检查清单中枚举的所有程序集是否都正确安装在计算机上。 每个程序集都通过其名称、版本号和处理器体系结构在清单中进行指定。 如果应用程序依赖于并行程序集，请检查这些程序集是否正确安装在计算机上，以便操作系统加载程序可以找到它们，如[程序集搜索序列](/windows/win32/SbsCs/assembly-searching-sequence)中所述。 请记住，64 位程序集不能在 32 位进程中加载，并且不能在 32 位操作系统上执行。

## <a name="example"></a>示例

假设我们有一个应用程序，appl.exe，这是通过使用视觉C++构建的。 该应用程序清单作为二进制资源 RT_MANIFEST（ID 等于 1）嵌入在 appl.exe 中，或存储为单独文件 appl.exe.manifest。 此清单的内容类似于下面这样：

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

对于操作系统加载程序，此清单指示 appl.exe 依赖于一个名为 Fabrikam.SxS.Library、版本是 2.0.20121.0 并且是为 32 位 x86 处理器体系结构而生成的程序集。 依赖的并行程序集可以作为共享程序集或私有程序集进行安装。

共享程序集的程序集清单安装在 %WINDIR%\WinSxS\Manifests\ 文件夹中。 它标识程序集并列出其内容（即，作为程序集一部分的 DLL）：

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

并行程序集还可以使用[发布服务器配置文件](/windows/win32/SbsCs/publisher-configuration-files)（也称为策略文件）全局重定向应用程序和程序集，以使用并行程序集的一个版本，而不是同一程序集的另一个版本。 可以在 %WINDIR%\WinSxS\Policies\ 文件夹中检查共享程序集的策略。 下面是一个示例策略文件：

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">

   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <dependency>
      <dependentAssembly>
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>
      </dependentAssembly>
   </dependency>
</assembly>
```

此策略文件指定请求获得此程序集的 2.0.10000.0 版本的任何应用程序或程序集都应改为使用 2.0.20121.0 版本（这是系统上安装的当前版本）。 如果在策略文件中指定了应用程序清单中提到的程序集版本，则加载程序会在 %WINDIR%\WinSxS\ 文件夹中查找清单中指定的此程序集的版本，如果未安装此版本，则加载会失败。 并且，如果未安装程序集版本 2.0.20121.0，则对于请求获得程序集版本 2.0.10000.0 的应用程序，加载会失败。

不过，程序集也可以作为私有并行程序集安装在已安装应用程序文件夹中。 如果操作系统未能找到作为共享程序集的程序集，则它会按以下顺序查找作为私有程序集的程序集：

1. 检查应用程序文件夹中具有名称程序集名称\<>.manifest 的清单文件。 在此示例中，加载程序尝试在包含 appl.exe 的文件夹中查找 Fabrikam.SxS.Library.manifest。 如果找到清单，则加载程序从应用程序文件夹加载程序集。 如果找不到程序集，则加载会失败。

1. 尝试打开包含\\appl.exe 的文件夹中\><程序集名称 = 文件夹，如果\\存在<程序集名称\>= 存在，请尝试在此文件夹中加载名称程序集名称\<>.manifest 的清单文件。 如果找到清单，加载程序将从\\<程序集名称\>+ 文件夹中加载程序集。 如果找不到程序集，则加载会失败。

有关加载程序如何搜索从属程序集的详细信息，请参阅[程序集搜索序列](/windows/win32/SbsCs/assembly-searching-sequence)。 如果加载程序未能找到作为私有程序集的依赖程序集，则加载会失败，并显示消息“系统无法执行指定的程序”。 若要解决此错误，请确保依赖程序集（以及作为它们一部分的 DLL）作为私有或共享程序集安装在计算机上。

## <a name="see-also"></a>另请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
