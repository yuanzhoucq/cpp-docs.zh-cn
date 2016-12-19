---
title: "演练：自动加载工具箱项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK], 借助反射添加控件"
  - "反射, 工具箱"
ms.assetid: b03c0d62-3be0-475f-b1d9-725dee993ad6
caps.latest.revision: 56
caps.handback.revision: 56
manager: "douge"
---
# 演练：自动加载工具箱项
本演练阐释了托管的 VSPackage 如何使用反射来自动加载所有其自身程序集提供的 <xref:System.Drawing.Design.ToolboxItem> 项。  
  
> [!NOTE]
>  向工具箱添加自定义控件的建议方式是，使用 Visual Studio SDK 随附的工具箱控件模板，此模板中包含自动加载支持。 保留本主题以实现向后兼容性、添加现有控件到工具箱和实现高级工具箱开发。  
>   
>  有关使用模板创建工具箱控件的详细信息，请参阅 [如何：创建使用 Windows 窗体的工具箱控件](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) 和 [创建 WPF 工具箱控件](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 本演练将指导你完成以下步骤：  
  
1.  通过使用 <xref:System.ComponentModel.ToolboxItemAttribute><xref:System.Drawing.ToolboxBitmapAttribute> 和 <xref:System.ComponentModel.DisplayNameAttribute>，在 VSPackage 对象中添加并正确注册所有“工具箱”控件。  
  
2.  创建以下两个控件，并将各自的图标添加到“工具箱”：  
  
    -   使用默认的 <xref:System.Drawing.Design.ToolboxItem> 类添加一个控件。  
  
    -   通过使用派生自 <xref:System.Drawing.Design.ToolboxItem> 类的自定义类添加另一个控件。  
  
3.  将 VSPackage 注册为提供具有 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 类的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
4.  使用反射生成一个列表，其中列出加载 VSPackage 时其提供的所有 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
5.  创建 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的处理程序。 执行此操作可保证正确加载 VSPackage 的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
6.  对 VSPackage 实现命令以强制重新初始化“工具箱”。  
  
## 系统必备  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[扩展 Visual Studio 概述](../Topic/Extending%20Visual%20Studio%20Overview.md)。  
  
## Visual Studio 包项目模板的位置  
 可在“新建项目”对话框中的三个不同位置找到 Visual Studio 包项目模板：  
  
1.  在“Visual Basic 扩展性”之下。 项目的默认语言为 Visual Basic。  
  
2.  在“C\# 扩展性”之下。 项目的默认语言为 C\#。  
  
3.  在“其他项目类型扩展性”之下。 项目的默认语言为 C\+\+。  
  
## 创建托管的 VSPackage  
  
#### 创建 LoadToolboxMembers VSPackage  
  
1.  创建名为 `LoadToolboxMembers` 的 VSPackage。 有关更多信息，请参见[演练：使用 Visual Studio 包模板创建菜单命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  添加菜单命令。  
  
     对于 Visual Basic，将该命令命名为 `Initialize LoadToolboxMembers VB`；对于 Visual C\#，命名为 `Initialize LoadToolboxMembers CS`。  
  
 如果使用多种语言按照本演练的步骤操作，则必须更新项目以消除所生成程序集的歧义。  
  
#### 消除 Visual Basic 和 Visual C\# Vspackage 的歧义  
  
1.  对于 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]：  
  
    -   在“解决方案资源管理器”中，打开项目属性，并选择“应用程序”选项卡。  
  
         将程序集名称更改为 `LoadToolboxMembersVB`，并将默认命名空间更改为 `Company.LoadToolboxMembersVB`。  
  
2.  对于 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]：  
  
    1.  在“解决方案资源管理器”中，打开项目属性，并选择“应用程序”选项卡。  
  
         将程序集名称更改为 `LoadToolboxMembersCS`，并将默认命名空间更改为 `Company.LoadToolboxMembersCS`。  
  
    2.  在代码编辑器中打开 LoadToolboxMembersPackage 类。  
  
         若要使用重构工具对现有命名空间进行重命名，请右键单击现有命名空间名称 `LoadToolboxMembers`，指向“重构”，然后单击“重命名”。 将名称更改为 `LoadToolboxMembersCS`。  
  
3.  保存所有更改。  
  
#### 添加支持的引用  
  
1.  在 LoadToolboxMembers 项目中，添加对 <xref:System.Drawing.Design?displayProperty=fullName> .NET Framework 组件的引用，如下所示。  
  
    1.  在“解决方案资源管理器”中，右键单击“LoadToolboxMembers”项目，然后单击“添加”和“引用”。  
  
    2.  在“引用”对话框的“.NET”选项卡上，双击“System.Drawing.Design”。  
  
2.  对于 Visual Basic，向已导入项目的命名空间列表添加以下命名空间：  
  
    -   Company.LoadToolboxMembersVB  
  
    -   系统  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
#### 测试生成的代码  
  
1.  在 Visual Studio 的实验性配置单元中，编译并启动 VSPackage。  
  
2.  在“工具”菜单上，单击“初始化 LoadToolboxMembers VB”或“初始化 LoadToolboxMembers CS”。  
  
     这会打开一个含有文本的消息框，文本指示已调用包的菜单项句柄。  
  
3.  关闭 [!INCLUDE[vs_current_short](../misc/includes/vs_current_short_md.md)] 的实验版本。  
  
## 创建工具箱控件  
 在本部分中，你将创建并注册用户控件 `Control1`，该控件声明了关联的默认“工具箱”项。 若要深入了解如何创作 Windows 窗体控件和 <xref:System.Drawing.Design.ToolboxItem> 类，请参阅[设计时开发 Windows 窗体控件](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
#### 创建将与默认 ToolboxItem 一起使用的“工具箱”控件  
  
1.  在“解决方案资源管理器”中，将 <xref:System.Windows.Forms.UserControl> 对象添加到 LoadToolboxMembers 项目，如下所示：  
  
    1.  在“解决方案资源管理器”中，右键单击“LoadToolboxMembers”项目，指向“添加”，然后单击“用户控件”。  
  
    2.  在“添加新项”对话框中，将名称更改为 `Control1.vb`（对于 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]）或 `Control1.cs`（对于 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]）。  
  
         若要深入了解如何向项目添加新项，请参阅 [NIB：如何：添加新项目项](http://msdn.microsoft.com/zh-cn/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  
  
     新控件将在设计视图中打开。  
  
2.  从“工具箱”中，将“按钮”控件（位于“公共控件”类别内）拖动到设计器。  
  
3.  双击刚创建的按钮。 这会为按钮的 <xref:System.Windows.Forms.Control.Click> 事件添加一个事件处理程序。 使用以下代码更新事件处理程序：  
  
     [!code-cs[LoadToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_1.cs)]
     [!code-vb[LoadToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_1.vb)]  
  
4.  修改控件的构造函数，以在调用 `InitializeComponent` 方法后设置按钮文本：  
  
     [!code-cs[LoadToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_2.cs)]
     [!code-vb[LoadToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_2.vb)]  
  
5.  将特性添加到文件，以使 VSPackage 可以查询提供的 <xref:System.Drawing.Design.ToolboxItem> 类：  
  
     [!code-cs[LoadToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_3.cs)]
     [!code-vb[LoadToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_3.vb)]  
  
6.  保存该文件。  
  
 在下列过程中，你将再创建并注册一个用户控件 `Control2`，并将创建和注册一个派生自 <xref:System.Drawing.Design.ToolboxItem> 类的关联自定义“工具箱”项 `Control2_ToolboxItem`。  
  
#### 使用派生自 ToolboxItem 的自定义类创建“工具箱”控件  
  
1.  再创建一个名为 `Control2` 的用户控件。 双击窗体以显示代码文件。  
  
2.  将 `System.Drawing.Design` 和 `System.Globalization` 添加到类中所用的命名空间。  
  
     [!code-cs[LoadToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_4.cs)]
     [!code-vb[LoadToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_4.vb)]  
  
3.  添加按钮和按钮单击事件处理程序，并按更新第一个控件的方式更新控件的构造函数。  
  
4.  向文件添加 <xref:System.ComponentModel.DisplayNameAttribute>、<xref:System.ComponentModel.DescriptionAttribute>、<xref:System.ComponentModel.ToolboxItemAttribute> 和 <xref:System.Drawing.ToolboxBitmapAttribute> 特性。  
  
     这些特性使 VSPackage 能够查询 <xref:System.Drawing.Design.ToolboxItem> 类。  
  
     有关如何编写自定义 <xref:System.Drawing.Design.ToolboxItem> 对象的详细信息和示例，请参阅 <xref:System.Drawing.Design.ToolboxItem> 引用页的讨论。  
  
     结合先前更改，你的第二个控件类应类似于以下代码。 在执行下一步之后才会定义符号 `Control2_ToolboxMenu`。  
  
     [!code-cs[LoadToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_5.cs)]
     [!code-vb[LoadToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_5.vb)]  
  
5.  创建名为 `Control2_ToolboxItem` 的类。 此 <xref:System.Drawing.Design.ToolboxItem> 是为第二个控件构造的，并已添加到“工具箱”。 此类必须应用有 `SerializableAttribute`。  
  
     [!code-cs[LoadToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_6.cs)]
     [!code-vb[LoadToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_6.vb)]  
  
6.  保存该文件。  
  
## 嵌入位图图标  
 先前使用的 <xref:System.Drawing.ToolboxBitmapAttribute> 的两个实例指示项目通过使用以下图标来表示两个控件：  
  
-   `Control1.bmp` 位于含有第一个控件的命名空间中。  
  
-   `Control2.bmp` 位于含有第二个控件的命名空间中。  
  
#### 为 ToolboxItem 嵌入位图图标  
  
1.  向项目添加两个新位图，如下所示。  
  
    1.  右键单击 `LoadToolboxMembers` 项目。  
  
    2.  指向“添加”，然后单击“新建项”。  
  
    3.  在“添加新项”对话框中，选择“位图文件”，然后命名文件 `Control1.bmp`。  
  
    4.  对第二个位图重复上述步骤，并将其命名 `Control2.bmp`。  
  
         执行此操作会在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 位图编辑器中打开每个位图。  
  
2.  将各图标的大小设置为 16 x 16，如下所示。  
  
    1.  对于每个位图，单击“视图”菜单上的“属性窗口”。  
  
    2.  在“属性”窗口中，将“高度”和“宽度”设为 16。  
  
3.  使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的位图编辑器为每个图标创建一个图像。  
  
4.  在“解决方案资源管理器”中，单击各个位图文件，然后在“属性”窗口中将“生成操作”属性为“嵌入的资源”。  
  
5.  保存所有打开的文件。  
  
## 修改 VSPackage 实现  
 必须修改 VSPackage 的默认实现，才能执行以下操作：  
  
-   注册支持，使其成为“工具箱”项提供程序。  
  
-   获取 VSPackage 支持的 <xref:System.Drawing.Design.ToolboxItem> 对象的列表。  
  
-   在处理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件时，加载“工具箱”[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
 下一过程演示了如何修改包实现。  
  
#### 修改包实现，使其成为 VSPackage 的“工具箱”项提供程序  
  
1.  在代码编辑器中打开 LoadToolboxMembersPackage.cs 或 LoadToolboxMembersPackage.vb 文件。  
  
2.  修改 `LoadToolboxMembersPackage` 类的声明，该类是解决方案中 <xref:Microsoft.VisualStudio.Shell.Package> 类的实现，如下所示。  
  
    1.  将以下命名空间指令添加到 `LoadToolboxMembersPackage` 类文件。  
  
         [!code-cs[LoadToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_7.cs)]
         [!code-vb[LoadToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_7.vb)]  
  
    2.  通过添加 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的实例，将 VSPackage 注册为 <xref:System.Drawing.Design.ToolboxItem> 类。  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的唯一参数是由 VSPackage 提供的 <xref:System.Drawing.Design.ToolboxItem> 版本。 更改此值可使 IDE 强制加载 VSPackage，即使它具有 <xref:System.Drawing.Design.ToolboxItem> 的较早缓存版本也是如此。  
  
    3.  将以下两个新 `private` 字段添加到 `LoadToolboxMembersPackage` 类：  
  
         一个名为 `ToolboxItemList` 的 <xref:System.Collections.ArrayList> 成员，用于承载 `LoadToolboxMembersPackage` 类所管理的 <xref:System.Drawing.Design.ToolboxItem> 对象的列表。  
  
         一个名为 `CategoryTab` 的 <xref:System.String>，它包含用于承载 `LoadToolboxMembersPackage` 类所管理的 <xref:System.Drawing.Design.ToolboxItem> 对象的“工具箱”类别或选项卡。  
  
     此修改得到的结果将类似于以下代码：  
  
     [!code-cs[LoadToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_8.cs)]
     [!code-vb[LoadToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_8.vb)]  
  
3.  展开“包成员”区域以修改 `Initialize` 方法来执行以下操作：  
  
    -   有关 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，请订阅 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
    -   调用 `CreateItemList` 方法来填充 <xref:System.Collections.ArrayList> 对象 `ToolboxItemList`。`ToolboxItemList` 将包含 `LoadToolboxMembersPackage` 托管的所有工具箱项的列表。  
  
     [!code-cs[LoadToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_9.cs)]
     [!code-vb[LoadToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_9.vb)]  
  
4.  添加 `CreateItemList` 和 `CreateToolboxItem` 两种方法，以使用元数据来构造可在 `LoadToolboxMembers` 程序集中使用的 <xref:System.Drawing.Design.ToolboxItem> 对象的实例，如下所示：  
  
     [!code-cs[LoadToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_10.cs)]
     [!code-vb[LoadToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_10.vb)]  
  
5.  实现 `OnRefreshToolbox` 方法以处理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
     `OnRefreshToolbox` 方法使用 <xref:System.Drawing.Design.ToolboxItem> 对象的列表，这些对象包含在 `LoadToolboxMembersPackage` 类的 `ToolboxItemList` 成员中。 它还将执行以下操作：  
  
    -   删除所有已在变量 `CategoryTab` 所定义的“工具箱”类别中存在的 <xref:System.Drawing.Design.ToolboxItem> 对象。  
  
    -   将 `ToolboxItemList` 中列出的所有 <xref:System.Drawing.Design.ToolboxItem> 对象的新实例添加到 VSProject 的类别选项卡。  
  
    -   将“工具箱”活动选项卡移动到 VSProject 的类别选项卡。  
  
     [!code-cs[LoadToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_11.cs)]
     [!code-vb[LoadToolboxMembers#11](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_11.vb)]  
  
    > [!NOTE]
    >  作为练习，可以开发一种机制来测试 VSPackage 或项的版本，并且只在 VSPackage 版本更改或 <xref:System.Drawing.Design.ToolboxItem> 的版本已更改时才进行更新。  
  
## 初始化工具箱  
  
#### 实现命令以初始化工具箱  
  
-   更改菜单项的命令处理程序方法 `MenuItemCallBack`，如下所示。  
  
    1.  将 `MenuItemCallBack` 的现有实现替换为以下代码：  
  
         [!code-cs[LoadToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_12.cs)]
         [!code-vb[LoadToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_12.vb)]  
  
## 生成并运行解决方案  
 通过使用在实验性配置单元中运行的 Visual Studio 的实例，可以运用本演练中的产品。  
  
#### 执行本演练  
  
1.  在 Visual Studio 的“生成”菜单上，单击“重新生成解决方案”。  
  
2.  按 F5 以在实验注册表配置单元中启动 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的第二个实例。  
  
     若要深入了解如何使用实验性配置单元，请参阅[实验实例](../Topic/The%20Experimental%20Instance.md)。  
  
3.  单击“工具”菜单。  
  
     菜单顶部应显示名为“Initialize ItemConfiguration VB”或“Initialize ItemConfiguration CS”的命令，以及带有数字 1 的图标。  
  
4.  创建新的 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] Windows 窗体应用程序。  
  
     应显示一个基于 <xref:System.Windows.Forms.Form> 的设计器。  
  
5.  将“工具箱”“LoadToolboxMembers Walkthrough VB”或“LoadToolboxMembers Walkthrough CS”类别中的一个新控件或全部两个控件拖动到设计器的窗体中。  
  
    > [!NOTE]
    >  若未显示“工具箱”，请在“视图”菜单上单击“工具箱”。 如果“工具箱”中未显示 VSPackage 的类别选项卡，则单击“工具”菜单上的“初始化 LoadToolboxMembers VB”或“初始化 LoadToolboxMembers CS”来重新初始化“工具箱”。  
  
6.  通过单击“生成”菜单上的“重新生成解决方案”，生成 Windows 应用程序。  
  
7.  通过单击“调试”菜单上的“启动”或“启动并调试”，运行此应用程序。  
  
8.  在应用程序运行时，单击添加到此应用程序的其中一个控件。  
  
     将出现一个消息框，显示 `"Hello world from Company.LoadToolboxMembers.Control1"` 或  `"Hello world from Company.LoadToolboxMembers.Control2"`。  
  
## 实现的分析  
  
### 创建工具箱控件  
 方法 `CreateItemList` 在查询可用“工具箱”控件的 `Assembly` 时使用分配给 `Control1` 和 `Control2` 的特性。  
  
-   <xref:System.ComponentModel.ToolboxItemAttribute> 执行以下两项功能：  
  
    -   <xref:System.ComponentModel.ToolboxItemAttribute> 到 `Control1` 和 `Control2` 的赋值，这指示各有一个工具箱控件。  
  
    -   <xref:System.ComponentModel.ToolboxItemAttribute> 构造函数的参数，这指示在将控件添加到“工具箱”时是使用默认的 <xref:System.Drawing.Design.ToolboxItem> 类还是派生自 <xref:System.Drawing.Design.ToolboxItem> 的自定义类。  
  
         分配给 `Control1` 的 <xref:System.ComponentModel.ToolboxItemAttribute> 的实例是通过使用 `true` 的参数创建的，这指示它在添加到“工具箱”是使用默认的 <xref:System.Drawing.Design.ToolboxItem> 类。  
  
         分配给 `Control2` 的 <xref:System.ComponentModel.ToolboxItemAttribute> 的实例是通过使用派生自 <xref:System.Drawing.Design.ToolboxItem>、`Control2_ToolboxItem` 的类的 <xref:System.Type> 创建的。  
  
-   <xref:System.Drawing.ToolboxBitmapAttribute> 类指定环境标识控件时所用的位图。  
  
     通过将程序集的“生成操作”属性设置为“嵌入的资源”来嵌入位图，这一操作可将位图置于程序集的命名空间内。 因此，可将 `Control1.bmp` 称为 `Company.LoadToolboxMembers.Control1.bmp`。  
  
     <xref:System.Drawing.ToolboxBitmapAttribute> 支持将此完整路径用作参数的构造函数。 例如，<xref:System.Drawing.ToolboxBitmapAttribute> 类无法通过使用 `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]` 应用到 `Control1`。  
  
     为支持灵活性，本演练所使用的构造函数将 <xref:System.Type> 类用作 <xref:System.Drawing.ToolboxBitmapAttribute> 构造函数的第一个参数。 用于标识位图文件的命名空间是从 <xref:System.Type> 获取的，且插入到了位图基名称的前面。  
  
     因为实现 <xref:Microsoft.VisualStudio.Shell.Package> 的 <xref:System.Type> 对象 \(`LoadToolboxMembers`\) 位于 `Company.LoadToolboxMembers` 命名空间中，因此 `[ToolboxBitmap(typeof(Control1), "Control1.bmp")]` 等同于 `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]`。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> 指定“工具箱”中控件的名称。  
  
### 注册工具箱控件提供程序  
 将 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 类应用于实现 <xref:Microsoft.VisualStudio.Shell.Package> 的类会影响生成的 VSPackage 的注册表设置。 若要深入了解 <xref:System.Drawing.Design.ToolboxItem> 提供程序的注册表设置，请参阅[注册工具箱支持功能](../misc/registering-toolbox-support-features.md)。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 环境将版本参数用于 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 构造函数，以管理向“工具箱”提供项的 VSPackage 的缓存。 在加载 VSPackage 以提供“工具箱”项后，将使用 VSPackage 的缓存版本，直到提供程序的注册版本更改。 因此，如果你想要在生成后修改本演练中的产品，请确保更改应用于 `AddToolboxItem` 的 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 构造函数的版本参数。 例如，`[ProvideToolboxItems(1)]` 应改为 `[ProvideToolboxItems(2)]`。 若未更改版本，则 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 环境不会加载任何所做的修改。  
  
 在本演练中，VSPackage 配置为仅提供支持默认剪贴板格式的**“工具箱”**控件。 有关默认剪贴板格式的列表，请参阅[扩展工具箱](../misc/extending-the-toolbox.md)。 如果你想要支持其他剪贴板格式，或决定不支持默认格式，请对 `LoadToolboxMembersPackage` 类应用特性 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute>。 若要深入了解如何注册“工具箱”控件提供程序，请参见 [高级工具箱控件开发](../misc/advanced-toolbox-control-development.md)。  
  
### 将控件添加到工具箱  
 `CreateItemList` 中的功能模拟了 <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> 中的可用内容。  
  
 `CreateItemList` 方法只检查实现 <xref:System.ComponentModel.IComponent> 接口的非抽象 <xref:System.Type> 对象。  
  
## 后续步骤  
 使用 <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A>（而不是 `CreateItemList`）会使本演练中的产品更可靠。  
  
 还可以修改 `CreateItemList`，以便根据 `LoadToolboxMembers` 程序集中内嵌的文本列表借助 <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> 将控件添加到“工具箱”。  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [注册工具箱支持功能](../misc/registering-toolbox-support-features.md)   
 [高级工具箱控件开发](../misc/advanced-toolbox-control-development.md)   
 [工具箱演练](../misc/toolbox-walkthroughs.md)