# New-TemporaryFile
A volte, negli script è necessario creare un file temporaneo. È possibile farlo facilmente con il cmdlet **New-TemporaryFile**:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp
<!--HONumber=Mar16_HO2-->
