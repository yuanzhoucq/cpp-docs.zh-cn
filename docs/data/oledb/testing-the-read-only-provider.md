---
title: "测试只读提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 调用"
  - "OLE DB 提供程序, 测试"
  - "测试提供程序"
  - "测试, OLE DB 提供程序"
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 测试只读提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为测试提供程序，需要一个使用者。  如果使用者可以与提供程序配合使用，它将很有帮助。  OLE DB 使用者模板是围绕 OLE DB 的瘦包装，并与提供程序 COM 对象配合使用。  因为使用者模板附带了源，所以用它们调试提供程序很容易。  使用者模板也是开发使用者应用程序的非常小且快速的方法。  
  
 本主题中的示例为测试使用者创建默认的“MFC 应用程序向导”应用程序。  测试应用程序是添加了 OLE DB 使用者模板代码的简单对话框。  
  
### 创建测试应用程序  
  
1.  在**“文件”**菜单上单击**“新建”**，再单击**“项目”**。  
  
2.  在“项目类型”窗格中，选择**“Visual C\+\+ 项目”**文件夹。  在“模板”窗格中，选择**“MFC 应用程序”**。  
  
3.  对于项目名称，输入 **TestProv** 再单击**“确定”**。  
  
     即会出现“MFC 应用程序向导”。  
  
4.  在**“应用程序类型”**页中选择“基于对话框”。  
  
5.  在**“高级功能”**页中选择“自动化”，再单击“完成”。  
  
> [!NOTE]
>  如果在 **CTestProvApp::InitInstance** 中添加 **CoInitialize**，应用程序不要求自动化支持。  
  
 通过在“资源视图”中选择 TestProv 对话框 \(IDD\_TESTPROV\_DIALOG\)，可以查看并编辑它。  将两个列表框（行集合中的每个字符串各有一个）放在对话框中。  当列表框被选定时按 Alt\+Enter 键，单击“样式”选项卡并清除“排序”复选框，以关闭两个列表框的排序属性。  另外，将“运行”按钮放在对话框中以获取文件。  已完成的“TestProv”对话框应该有两个列表框，分别标记为“String 1”和“String 2”；它还应有**“确定”**、“取消”和“运行”按钮。  
  
 打开对话框类的头文件（在此例中为 TestProvDlg.h）。  将以下代码添加到头文件中（在任何类声明的外部）：  
  
```  
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
class CProvider   
{  
// Attributes  
public:  
   char   szField1[16];  
   char   szField2[16];  
  
   // Binding Maps  
BEGIN_COLUMN_MAP(CProvider)  
   COLUMN_ENTRY(1, szField1)  
   COLUMN_ENTRY(2, szField2)  
END_COLUMN_MAP()  
};  
```  
  
 代码表示定义哪些列将在行集合中的用户记录。  当客户端调用 **IAccessor::CreateAccessor** 时，它使用这些项指定要绑定的列。  OLE DB 使用者模板还允许动态绑定列。  COLUMN\_ENTRY 宏是 PROVIDER\_COLUMN\_ENTRY 宏的客户端版本。  两个 COLUMN\_ENTRY 宏指定两个字符串的序号、类型、长度和数据成员。  
  
 按住 Ctrl 键并双击“运行”按钮，为“运行”按钮添加处理函数。  将以下代码放在函数中：  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
      return;  
  
   while (table.MoveNext() == S_OK)  
   {  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
   }  
}  
```  
  
 `CCommand`、`CDataSource` 和 `CSession` 类都属于 OLE DB 使用者模板。  每个类模仿提供程序中的一个 COM 对象。  `CCommand` 对象将头文件中声明的 `CProvider` 类作为模板参数使用。  `CProvider` 参数表示用于访问来自提供程序的数据的绑定。  以下是数据源、会话和命令的 `Open` 代码：  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 打开每个类的行创建提供程序中的每个 COM 对象。  若要定位提供程序，请使用提供程序的 ProgID。  可以从系统注册表中获取 ProgID，或者在 MyProvider.rgs 文件中查找（打开提供程序的目录并搜索 ProgID 项）。  
  
 MyProv 示例中包括 myData.txt 文件。  若要创建自己的文件，请使用编辑器并键入偶数个字符串，在每个字符串之间按 Enter 键。  如果移动文件，请更改路径名。  
  
 将字符串“c:\\\\samples\\\\myprov\\\\myData.txt”传递到 `table.Open` 行中。  如果进入并单步执行 `Open` 调用，您将看到该字符串被传递给提供程序中的 `SetCommandText` 方法。  注意 `ICommandText::Execute` 方法使用了该字符串。  
  
 若要提取数据，请对表调用 `MoveNext`。  `MoveNext` 调用 **IRowset::GetNextRows**、`GetRowCount` 和 `GetData` 函数。  当没有更多的行时（即行集合中的当前位置大于 `GetRowCount`），循环终止：  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 注意当没有更多的行时，提供程序返回 **DB\_S\_ENDOFROWSET**。  **DB\_S\_ENDOFROWSET** 值不是错误。  应该总是对照 `S_OK` 进行检查以取消数据获取循环并且不使用 SUCCEEDED 宏。  
  
 现在应该能够生成和测试程序。  
  
## 请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)