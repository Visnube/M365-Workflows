📋 Required Columns (default, edit in code as needed)
ALDI DATA: Article No., Article Name, Net Weight

SUPPLIER DATA: Supplier Name, Country, Contact Person

LOGISTICS COST: Cost Type, Amount, Currency

🧑‍💻 How to Set Up
Create a new (empty) Excel workbook.

Press ALT + F11 to open the VBA editor.

Insert a new Module and copy the code below into it.

Back in Excel, go to Developer Tab → Insert → Button (Form Control), draw the button on the sheet, and assign it to Check_IFQ_Tool.

Rename the button to Check IFQ.

Sub Check_IFQ_Tool()
    Dim fd As FileDialog
    Dim FileChosen As Integer
    Dim FilePath As String
    Dim wb As Workbook
    Dim wsNames As Variant
    Dim checkCols As Variant
    Dim ws As Worksheet
    Dim col As Variant
    Dim row As Long, lastRow As Long
    Dim missingInfo As String
    Dim cell As Range
    Dim i As Integer

    ' File Picker
    Set fd = Application.FileDialog(msoFileDialogFilePicker)
    fd.Title = "Select the IFQ Excel file to check"
    fd.Filters.Clear
    fd.Filters.Add "Excel Files", "*.xls; *.xlsx"
    FileChosen = fd.Show
    If FileChosen <> -1 Then
        MsgBox "No file selected. Cancelled.", vbExclamation
        Exit Sub
    End If
    FilePath = fd.SelectedItems(1)

    Application.ScreenUpdating = False

    ' Open file in background
    Set wb = Workbooks.Open(FilePath, ReadOnly:=True)

    wsNames = Array("ALDI DATA", "SUPPLIER DATA", "LOGISTICS COST")
    checkCols = Array( _
        Array("Article No.", "Article Name", "Net Weight"), _
        Array("Supplier Name", "Country", "Contact Person"), _
        Array("Cost Type", "Amount", "Currency") _
    )
    
    missingInfo = ""
    
    For i = LBound(wsNames) To UBound(wsNames)
        On Error Resume Next
        Set ws = wb.Sheets(wsNames(i))
        If ws Is Nothing Then
            missingInfo = missingInfo & "Tab '" & wsNames(i) & "' not found!" & vbCrLf
            On Error GoTo 0
            GoTo NextWS
        End If
        On Error GoTo 0
        
        lastRow = ws.Cells(ws.Rows.Count, 1).End(xlUp).Row
        
        For Each col In checkCols(i)
            ' Find column by name (first row)
            Dim colNum As Variant
            colNum = Application.Match(col, ws.Rows(1), 0)
            If IsError(colNum) Then
                missingInfo = missingInfo & wsNames(i) & ": Column '" & col & "' not found!" & vbCrLf
            Else
                ' Check all rows in that column for missing values
                For row = 2 To lastRow
                    Set cell = ws.Cells(row, colNum)
                    If Trim(cell.Value) = "" Then
                        missingInfo = missingInfo & wsNames(i) & ": Missing '" & col & "' in row " & row & vbCrLf
                    End If
                Next row
            End If
        Next col
NextWS:
        Set ws = Nothing
    Next i

    wb.Close False
    Application.ScreenUpdating = True

    If missingInfo = "" Then
        missingInfo = "All required data are present. Great!"
    End If

    ' ==== Generate Email (Outlook required) ====
    Dim OutlookApp As Object
    Dim OutlookMail As Object
    Set OutlookApp = CreateObject("Outlook.Application")
    Set OutlookMail = OutlookApp.CreateItem(0)
    
    With OutlookMail
        .To = ""  ' Optionally enter recipient
        .Subject = "Missing Data in IFQ"
        .Body = "Automatic check of your IFQ file found the following issues:" & vbCrLf & vbCrLf & missingInfo
        .Display   ' Shows email (does NOT auto-send)
    End With
    
    Set OutlookMail = Nothing
    Set OutlookApp = Nothing

    MsgBox "Check complete. Email prepared.", vbInformation
End Sub

📝 Notes
You can change the tab names and columns to match your IFQ template.

The result is always shown and added to a ready-to-send Outlook email.
