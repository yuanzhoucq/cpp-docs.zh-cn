---
title: /TLBID（指定类型库的资源 ID）
ms.date: 11/04/2016
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
ms.openlocfilehash: c52bfb9e4b6d0e94cecb77c766ac9e82b52f1e66
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820599"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID（指定类型库的资源 ID）

```
/TLBID:id
```

## <a name="arguments"></a>自变量

*id*<br/>
链接器创建类型库为用户指定的值。 它将替代默认资源 ID 为 1。

## <a name="remarks"></a>备注

在编译时使用的属性的程序，链接器将创建一个类型库。 链接器将分配到类型库的资源 ID 为 1。

如果此资源 ID 与一个现有资源冲突，你可以使用 /TLBID 指定其他 ID。 可以将传递到的值的范围`id`为 1 到 65535。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**嵌入的 IDL**属性页。

1. 修改**TypeLib 资源 ID**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
