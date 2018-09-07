##Disk Space
```bash
df -h
```
##Folders/Files size
```bash
du -sh */
```
##Bulk chmod
Change permission to all files/folders

To change all the directories to 755 (drwxr-xr-x):
```bash
find /opt/lampp/htdocs -type d -exec chmod 755 {} \;
```
To change all the files to 644 (-rw-r--r--):
```bash
find /opt/lampp/htdocs -type f -exec chmod 644 {} \;
```
##Replce Text in File
```bash
sed -i 's/original/new/g' file.txt
```
Explanation:

* sed = Stream EDitor
* -i = in-place (i.e. save back to the original file)
* The command string:
    * s = the substitute command
    * original = a regular expression describing the word to replace (or just the word itself)
    * new = the text to replace it with
    * g = global (i.e. replace all and not just the first occurrence)
* file.txt = the file name


##Search Text in Files
Do the following:
```bash
grep -rnw 'directory' -e "pattern"
```
Where:

`-r` or `-R` is recursive

`-n` is line number

`-w` stands match the whole word

`-l` (letter L) can be added to have just the file name

Along with these, `--exclude` or `--include` parameter could be used for efficient searching. Something like below:
```bash
grep --include=\*.{c,h} -rnw 'directory' -e "pattern"
```
This will only search through the files which have .c or .h extensions. Similarly a sample use of `--exclude`:
```bash
grep --exclude=*.o -rnw 'directory' -e "pattern"
```
Above will exclude searching all the files ending with `.o` extension. Just like exclude file it's possible to exclude/include directories through `--exclude-dir` and `--include-dir` parameter, the following shows how to integrate `--exclude-dir`:
```bash
grep --exclude-dir={dir1,dir2,*.dst} -rnw 'directory' -e "pattern"
```

For more options :
```bash
man grep
```