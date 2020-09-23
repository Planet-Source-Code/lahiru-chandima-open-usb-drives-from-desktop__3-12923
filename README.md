<div align="center">

## Open USB drives from desktop


</div>

### Description

This article demonstrates how to create a simple program which can open USB drives connected to the computer from the desktop.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[lahiru chandima](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/lahiru-chandima.md)
**Level**          |Intermediate
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__3-7.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/lahiru-chandima-open-usb-drives-from-desktop__3-12923/archive/master.zip)





### Source Code

```
To open a USB drive connected to your Windows installed computer, you have to go to My Computer. But, with this simple program, you can do it from your desktop. Also,if there are multiple USB drives connected, it will give a window to choose the drive you need to open.
Also,if you double click a pen drive icon in My Computer, there is a risk that the viruses that may be in the pen drive will infect your computer by auto running. But, there is no such risk when you use this program.
Here is the main code
int APIENTRY _tWinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPTSTR lpCmdLine, int nCmdShow)
{
driveselectdlg dlg;
CString driveletter;
POSITION pos;
LPWSTR lable=new WCHAR[50];
UINT drivetype;
DWORD logicaldrives, devider;
logicaldrives=GetLogicalDrives();
devider=8;
for(int i=0; i<10; i++)
{
driveletter=finddrive(devider);
devider*=2;
drivetype=GetDriveType(driveletter);
if(drivetype==DRIVE_REMOVABLE)
{
dlg.drivelist.AddTail(driveletter);
GetVolumeInformation(driveletter, lable, 50, NULL, NULL, NULL, NULL, 0);
dlg.lablelist.AddTail(lable);}}
if(dlg.lablelist.GetSize()==0)
{
::MessageBox(0, TEXT("No pen drive detected!"), TEXT("Message"), 0);
return 0;}
if(dlg.lablelist.GetSize()==1)
{
pos=dlg.drivelist.GetHeadPosition();
ShellExecute(NULL,TEXT("open"), dlg.drivelist.GetNext(pos), NULL, NULL, SW_SHOWMAXIMIZED);
return 0;}
if(dlg.DoModal()==IDOK)
{
pos=dlg.drivelist.GetHeadPosition();
for(int i=0; i<(dlg.selection-1); i++)
{
dlg.drivelist.GetNext(pos);}
ShellExecute(NULL,TEXT("open"), dlg.drivelist.GetNext(pos), NULL, NULL, SW_SHOWMAXIMIZED);}
return 0;}
To view the full article and download the source code visit http://www.frostcode.info/example-projects/open-usb-drives.html.
```

