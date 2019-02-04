# Search All Files and folders in directory

-----------------------------------------------------------------------------------------------------------------------------------

## Search All Files and folders in directory
  - use below function to search all the files and folders in given path
<pre><code>
findAllFileAndDir(CString strFolderPath, vector<CString>& vecDirNameLst, vector<CString>& vecFileNameLst)
{
	HANDLE hFind = INVALID_HANDLE_VALUE;
	WIN32_FIND_DATA fd;
	ZeroMemory(&fd, sizeof(WIN32_FIND_DATA));
	LARGE_INTEGER filesize;
	CString strFolderName;
	strFolderName = strImgFolder + L"*.*";
	hFind = FindFirstFile(strFolderName, &fd);
	vecDirNameLst.clear();
	vecFileNameLst.clear();
	vector<CString> vecStr;
	do
	{
		if ((fd.dwFileAttributes & FILE_ATTRIBUTE_DIRECTORY)/*&& strcmp(fd.cFileName, ".") && strcmp(fd.cFileName, "..")*/)
		{
			//read all directory
      			vecDirNameLst.push_back(fd.cFileName);
		}
		else
		{
			//read all types of files
      			vecFileNameLst.push_back(fd.cFileName);
		}
	} while (FindNextFile(hFind, &fd) != 0);
	FindClose(hFind);
}
</code></pre>
