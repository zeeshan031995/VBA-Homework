# VBA-Homework
Sub Stockmarket():
Dim volume As Double
Dim lastrow As Long
Dim OpenPrice As Double
Dim ClosePrice As Double
Dim Summary_Table As Integer
Dim Yearchng As Double
Dim percentchng As Double
For Each ws In Worksheets

ws.Range("I1").Value = "Ticker"
ws.Range("J1").Value = "Year Change"
ws.Range("K1").Value = "% Change"
ws.Range("L1").Value = "Total Volume"

volume = 0
lastrow = ws.Cells(Rows.Count, 1).End(xlUp).Row
Summary_Table = 2
OpenPrice = Range("C2").Value
For i = 2 To lastrow
If ws.Cells(i + 1, 1).Value <> ws.Cells(i, 1).Value Then
ws.Cells(Summary_Table, 9).Value = ws.Cells(i, 1).Value
volume = volume + ws.Cells(i, 7).Value
ws.Cells(Summary_Table, 12).Value = volume
ClosePrice = ws.Cells(i, 6).Value
Yearchng = ClosePrice - OpenPrice
    If ws.Cells(i + 1, 3).Value > 0 Then
    OpenPrice = ws.Cells(i + 1, 3).Value
    End If


ws.Cells(Summary_Table, 10).Value = Yearchng
percentchng = Round(((Yearchng / OpenPrice) * 100), 2)
ws.Cells(Summary_Table, 11).Value = "%" & percentchng

Summary_Table = Summary_Table + 1
volume = 0
ClosePrice = 0



Else
volume = volume + ws.Cells(i, 7).Value
End If
Next i
Next ws
End Sub

