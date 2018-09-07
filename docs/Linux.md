##Display All Permissions

Display all the permissions on a path:
```bash
namei -om /path/to/check
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