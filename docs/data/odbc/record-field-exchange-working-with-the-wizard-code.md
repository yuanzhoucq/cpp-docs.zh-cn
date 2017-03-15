---
title: "记录字段交换：使用向导代码 | Microsoft Docs"
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
  - "DoFieldExchange 方法, 重写"
  - "字段数据成员"
  - "字段数据成员, 声明"
  - "m_nFields 数据成员"
  - "m_nFields 数据成员, 初始化"
  - "m_nParams 数据成员"
  - "m_nParams 数据成员, 初始化"
  - "ODBC, RFX"
  - "重写, DoFieldExchange"
  - "RFX (ODBC), 实现"
  - "RFX (ODBC), 向导代码"
  - "Unicode, 带有数据库类"
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 记录字段交换：使用向导代码
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明“MFC 应用程序向导”和“添加类”（详见 [添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md) 中的介绍）为支持 RFX 而编写的代码，同时还介绍了如何修改这些代码。  
  
> [!NOTE]
>  本主题适用于从 `CRecordset` 派生的类，这些类中尚未实现批量取行。  如果使用的是批量取行，则实现批量记录字段交换 \(Bulk RFX\)。  Bulk RFX 与 RFX 类似。  若要了解其中的差别，请参见[记录集：批量获取记录 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 当您用“MFC 应用程序向导”或“添加类”创建记录集类时，向导根据您在向导中所做的数据源、表和列选择，为您编写下列与 RFX 相关的元素：  
  
-   记录集类中记录集字段数据成员的声明  
  
-   `CRecordset::DoFieldExchange` 的重写  
  
-   记录集类构造函数中记录集字段数据成员的初始化  
  
##  <a name="_core_the_field_data_member_declarations"></a> 字段数据成员声明  
 向导在 .h 文件中写记录集类声明，类似于下面 `CSections` 类的声明：  
  
```  
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
  
 如果要添加参数数据成员或您自己绑定的新字段数据成员，将它们添加在向导生成的参数数据成员后面。  
  
 同样，注意向导重写 `CRecordset` 类的 `DoFieldExchange` 成员函数。  
  
##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 重写  
 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 是 RFX 的核心。  框架一旦需要将数据从数据源移动到记录集或从记录集移动到数据源，就会调用 `DoFieldExchange`。  `DoFieldExchange` 还支持通过 [IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md) 和 [IsFieldNull](../Topic/CRecordset::IsFieldNull.md) 成员函数获取有关字段数据成员的信息。  
  
 以下是对 `CSections` 类的 `DoFieldExchange` 重写。  向导在 .cpp 文件中为记录集类编写该函数。  
  
```  
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
  
 注意该函数的以下主要功能：  
  
-   函数的这部分称为“字段映射”。  
  
-   通过 `pFX` 指针调用 `CFieldExchange::SetFieldType`。  该调用指定：一直到 `DoFieldExchange` 结束时的所有 RFX 函数调用或对 `SetFieldType` 的下一个调用都是输出列。  有关更多信息，请参见 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)。  
  
-   对 `RFX_Text` 全局函数的几个调用，即每个字段数据成员一个调用（此示例中它们全部为 `CString` 变量）。  这些调用指定数据源上的列名与字段数据成员之间的关系。  RFX 函数执行实际的数据传输。  类库为所有通用数据类型提供 RFX 函数。  有关 RFX 函数的更多信息，请参见 [记录字段交换：使用 RFX 函数](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。  
  
    > [!NOTE]
    >  结果集中的列顺序必须与 `DoFieldExchange` 中 RFX 函数调用的顺序相匹配。  
  
-   指向 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 对象的 `pFX` 指针，框架在调用 `DoFieldExchange` 时传递该对象。  `CFieldExchange` 对象指定 `DoFieldExchange` 要执行的操作、传输的方向以及其他上下文信息。  
  
##  <a name="_core_the_recordset_constructor"></a> 记录集构造函数  
 向导写的记录集构造函数包含两个与 RFX 相关的操作：  
  
-   初始化每个字段数据成员  
  
-   初始化包含字段数据成员数的 [m\_nFields](../Topic/CRecordset::m_nFields.md) 数据成员。  
  
 `CSections` 记录集构造函数的示例类似于：  
  
```  
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
>  如果手动添加任何字段数据成员（如动态绑定新列时可能要做的），则必须增加 `m_nFields`。  通过追加另一代码行来完成该操作，如：  
  
```  
m_nFields += 3;  
```  
  
 这是用于添加三个新字段的代码。  如果添加任何参数数据成员，则必须初始化 [m\_nParams](../Topic/CRecordset::m_nParams.md) 数据成员，该数据成员包含参数数据成员的数目。  将 `m_nParams` 初始化放在括号外。  
  
## 请参阅  
 [记录字段交换 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)