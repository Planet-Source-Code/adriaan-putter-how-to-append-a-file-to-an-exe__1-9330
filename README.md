<div align="center">

## How to Append a file to an EXE


</div>

### Description

This is just to show you how to append a file to an executable. Could be handy if you wanna save maybe a tag to your exe file. Have not test it with very large files but small file works perfectly.
 
### More Info
 
There could be problems with large files, I dont know.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Adriaan Putter](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/adriaan-putter.md)
**Level**          |Beginner
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0, VB Script, ASP \(Active Server Pages\) 
**Category**       |[Files/ File Controls/ Input/ Output](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files-file-controls-input-output__1-3.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/adriaan-putter-how-to-append-a-file-to-an-exe__1-9330/archive/master.zip)





### Source Code

```
Private Sub AppendToExe(exefile$,filetoappend$)
  Open filetoappend$ For Binary As #1
  filedata$ = String(LOF(1), " ")
  Get #1, , filedata$
  Close #1
  Open exefile$ For Binary As #1
  f = LOF(1)
  Seek #1, f + 1
  Put #1, , "WAP"   'any identifer
  Put #1, , filedata$
  Close #1
End Sub
Private Sub ExtractFromExe(exefile$,filetoextr$)
  Open exefile$ For Binary As #1
  filedata$ = String(LOF(1), " ")
  Get #1, , filedata$
  Close #1
  pos = InStr(1, filedata$, "WAP")
  f$ = Mid$(filedata$, pos + 3)
  Open filetoextr$ For Binary As #2
  Put #2, , f$
  Close #2
End Sub
```

