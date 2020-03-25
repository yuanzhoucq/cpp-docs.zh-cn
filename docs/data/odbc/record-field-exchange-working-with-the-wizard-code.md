---
title: 记录字段交换：使用向导代码
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 08d58561e0fb9305ff3a8d6aa6a62eb24d9b9d25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213039"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>记录字段交换：使用向导代码

> [!NOTE]
> MFC ODBC 使用者向导在 Visual Studio 2019 及更高版本中不可用。 你仍可以手动创建使用者。

本主题介绍 MFC 应用程序向导和“添加类”（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）编写的用于支持 RFX 的代码，以及你可能需要如何更改此代码。

> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的类，其中尚未实现批量提取行。 如果使用批量提取行，则将实现批量记录字段交换（批量 RFX）。 批量 RFX 与 RFX 类似。 若要了解差异，请参阅[记录集：批量提取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

使用 MFC 应用程序向导或“添加类”创建记录集类时，向导将根据你在向导中选择的数据源、表和列选项编写以下与 RFX 相关的元素：

- 记录集类中记录集字段数据成员的声明

- `CRecordset::DoFieldExchange` 的替代

- 记录集类构造函数中记录集字段数据成员的初始化

##  <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a> 字段数据成员声明

向导将在 .h 文件中编写记录集类声明，类似于类 `CSections` 的以下内容：

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

如果要添加你自己绑定的参数数据成员或新字段数据成员，请在向导生成的成员后添加它们。

另请注意，向导会替代 `CRecordset` 类的 `DoFieldExchange` 成员函数。

##  <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 替代

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 是 RFX 的核心。 框架会在任何需要的时候调用 `DoFieldExchange` 来将数据从数据源移动到记录集或从记录集移动到数据源。 `DoFieldExchange` 还支持通过 [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) 和 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) 成员函数来获取有关字段数据成员的信息。

以下 `DoFieldExchange` 替代适用于 `CSections` 类。 向导会将函数写入记录集类的 .cpp 文件中。

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

请注意此函数的以下主要功能：

- 函数的此部分称为字段映射。

- 通过 `pFX` 指针调用 `CFieldExchange::SetFieldType`。 此调用指定直到 `DoFieldExchange` 结束或下一次调用 `SetFieldType` 之前所有 RFX 函数调用都是输出列。 有关详细信息，请参阅 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

- 多次调用 `RFX_Text` 全局函数 - 每个字段数据成员一次（示例中所有的成员都是 `CString` 变量）。 这些调用指定数据源上的列名称与字段数据成员之间的关系。 RFX 函数执行实际的数据传输。 类库为所有常见数据类型提供 RFX 函数。 有关 RFX 函数的详细信息，请参阅[记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。

    > [!NOTE]
    >  结果集中列的顺序必须与 `DoFieldExchange` 中 RFX 函数调用的顺序匹配。

- 当它调用 `DoFieldExchange` 时框架传递的 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 对象的 `pFX` 指针。 `CFieldExchange` 对象指定 `DoFieldExchange` 要执行的操作、传输方向和其他上下文信息。

##  <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a> 记录集构造函数

向导编写的记录集构造函数包含两个与 RFX 相关的操作：

- 初始化每个字段数据成员

- 初始化 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 数据成员，其中包含字段数据成员的数量

`CSections` 记录集示例的构造函数如下所示：

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
>  如果手动添加任何字段数据成员，就像如果动态绑定新列一样，则必须递增 `m_nFields`。 通过追加另一行代码来执行此操作，例如：

```cpp
m_nFields += 3;
```

这是用于添加三个新字段的代码。 如果添加任何参数数据成员，则必须初始化 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 数据成员，其中包含参数数据成员的数量。 将 `m_nParams` 初始化放置在括号外。

## <a name="see-also"></a>请参阅

[记录字段交换 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
